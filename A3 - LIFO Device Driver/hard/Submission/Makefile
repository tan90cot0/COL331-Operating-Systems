CONFIG_MODULE_SIG=n

BINARY     := mychardev
KERNEL      := /lib/modules/$(shell uname -r)/build
ARCH        := x86
C_FLAGS     := -Wall -Wframe-larger-than=1100000
KMOD_DIR    := $(shell pwd)
TARGET_PATH := /lib/modules/$(shell uname -r)/kernel/drivers/char

OBJECTS := main.o

ccflags-y += $(C_FLAGS)

obj-m += $(BINARY).o

$(BINARY)-y := $(OBJECTS)

$(BINARY).ko:
	make -C $(KERNEL) M=$(KMOD_DIR) modules

install:
	cp $(BINARY).ko $(TARGET_PATH)
	depmod -a

uninstall:
	rm $(TARGET_PATH)/$(BINARY).ko
	depmod -a

clean:
	make -C $(KERNEL) M=$(KMOD_DIR) clean