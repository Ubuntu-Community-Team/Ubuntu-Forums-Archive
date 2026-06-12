---
title: "Failure to create sample module"
date: 2009-06-18
forum: General Help
---

### Post by Rbro on 2009-06-18
I am simply trying to make a standard "Hello world" module, as I am learning about Linux device drivers.

My module goes like this:

#include <linux/init.h>
#include <linux/module.h>
MODULE_LICENSE("Dual BSD/GPL");

static int hello_init(void)
{
	printk(KERN_ALERT "Hello, world\n");
	return 0;
}

static void hello_exit(void)
{
	printk(KERN_ALERT "Goodbye, cruel world\n");
}

module_init(hello_init);
module_exit(hello_exit);



My Makefile goes like this:


obj-m += hello.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean



My error is this:

dahsar@UbuntuBook:~/drivers$ make
make -C /lib/modules/2.6.28-11-generic/build M=/home/dahsar/drivers modules
make: *** /lib/modules/2.6.28-11-generic/build: No such file or directory.  Stop.
make: *** [all] Error 2


I clearly see build in that directory. However it seems to be a file, not a directory of its own. What am I doing wrong?

Any help will be much appreciated.

Thanks,

Rbro

---

