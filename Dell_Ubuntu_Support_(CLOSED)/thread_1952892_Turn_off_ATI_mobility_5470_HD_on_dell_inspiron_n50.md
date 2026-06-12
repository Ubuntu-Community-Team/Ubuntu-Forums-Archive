---
title: "Turn off ATI mobility 5470 HD on dell inspiron n5010"
date: 2012-04-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ankushkale1 on 2012-04-05
hi friends,

I have dell laptop with ati mobility 5470 hd graphics card.

Laptop starts heating becoz of graphics card.When i play hd movies temperature reaches to 75+ ( i seen that in conky) i tried aticonfig commands to manually turn down core & memory clocks but not supported.
well i also cant control my fan speeds too (tried sensors-detect but no info about fan so i cant control fan speed too).

Also there is no option in BIOS to turn off graphics card.

i googled & found one code for lenovo laptop for turn off ati cards is that work for me too?

here is code:

```
/* Linux kernel module that disables the discrete graphics board for Lenovo
 * U330. Other lenovo laptops could work, but I don't know.
 *
 * Copyright (c) 2009: Sylvain Joyeux <sylvain.joyeux@m4x.org>
 */
#include <acpi/acpi.h>

MODULE_LICENSE("GPL");

static acpi_handle root_handle;

static int __init kill_ati(void)
{
    int i;
    acpi_status status;
    // The device handle
    acpi_handle handle;
    // The package elements
    union acpi_object package_elements[3];
    // The arguments to ATPX
    union acpi_object atpx_arg_elements[2];
    struct acpi_object_list atpx_arg;
    // For the return value of ATPX
    struct acpi_buffer buffer = { ACPI_ALLOCATE_BUFFER, NULL };

    status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.ATPX", &handle);
    if (ACPI_FAILURE(status))
    {
        status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.XTPX", &handle);
        if (ACPI_FAILURE(status))
        {
            printk("lenovo_acpi: cannot get ACPI handle: %s\n", acpi_format_exception(status));
            return -ENOSYS;
        }
        printk("lenovo_acpi: in discrete graphics mode\n");
        return 0;
    }

    for (i = 0; i < 3; ++i)
    {
        package_elements[i].type = ACPI_TYPE_INTEGER;
        package_elements[i].integer.value = 0;
    }

    atpx_arg.count = 2;
    atpx_arg.pointer = &atpx_arg_elements[0];

    atpx_arg_elements[0].type = ACPI_TYPE_INTEGER;
    atpx_arg_elements[0].integer.value = 2;

    atpx_arg_elements[1].type = ACPI_TYPE_PACKAGE;
    atpx_arg_elements[1].package.count = 3;
    atpx_arg_elements[1].package.elements = &package_elements[0];
    
    status = acpi_evaluate_object(handle, NULL, &atpx_arg, &buffer);
    if (ACPI_FAILURE(status))
    {
        printk("lenovo_acpi: ATPX method call failed: %s\n", acpi_format_exception(status));
        return -ENOSYS;
    }
    kfree(buffer.pointer);

    printk("lenovo_acpi: disabled the discrete graphics card\n");
    return 0;
}

static void dummy(void)
{
}

module_init(kill_ati);
module_exit(dummy);
```i am using Ubuntu 12.04 beta 2

Eagrly wating for reply guys..

---

### Post by ankushkale1 on 2012-04-06
Hi,

**Guys plz post your conky temperature readings..**

mine are 50-55C CPU & 60-65C GPU ( core i5 & ati mobility 5470 HD) in normal working..

& **suggest me good thermal paste ( i live in INDIA ) , I have some white colored thermal paste.**

I opened & cleaned my laptop so now temperature has gone down by 10C.** I saw there was thick gray paste on CPU & GPU** ,i applied my white thermal paste (i think this paste is silicon .... something) on that previous gray paste. **So can i remove that old gray paste ** **& fully apply mine white paste?**

---

### Post by gruebler on 2012-04-26
> **ankushkale1 said:**
> Hi,

**Guys plz post your conky temperature readings..**

mine are 50-55C CPU & 60-65C GPU ( core i5 & ati mobility 5470 HD) in normal working..

& **suggest me good thermal paste ( i live in INDIA ) , I have some white colored thermal paste.**

I opened & cleaned my laptop so now temperature has gone down by 10C.** I saw there was thick gray paste on CPU & GPU** ,i applied my white thermal paste (i think this paste is silicon .... something) on that previous gray paste. **So can i remove that old gray paste ** **& fully apply mine white paste?**


Use thermal compound with silver in it. tech guys like arctic silver the most, but i don't think brands are very important.
also, when i took apart my n5010, on the gpu heatsink was a thermal pad, which i ripped off. problem: there is a gap between heatsink and gpu of ca. 0.5-1 mm which can not be filled by thermal compound (grease). dell used the thick (min 1mm) thermal pad, to make contact between gpu and heatsink. so i ordered some thermal pad for the gpu. for the cpu i will use thermal compound with silver. an alternative would be to place a small copper plate (or shim) between gpu and heatsink. of course, you need to put thermal compound between gpu and plate, and between plate and heatsink...
anyway, not filling the gap caused quite immediate shutdown.

---

### Post by forbidden404 on 2012-04-29
> **ankushkale1 said:**
> hi friends,

I have dell laptop with ati mobility 5470 hd graphics card.

Laptop starts heating becoz of graphics card.When i play hd movies temperature reaches to 75+ ( i seen that in conky) i tried aticonfig commands to manually turn down core & memory clocks but not supported.
well i also cant control my fan speeds too (tried sensors-detect but no info about fan so i cant control fan speed too).

Also there is no option in BIOS to turn off graphics card.

i googled & found one code for lenovo laptop for turn off ati cards is that work for me too?

here is code:

```
/* Linux kernel module that disables the discrete graphics board for Lenovo
 * U330. Other lenovo laptops could work, but I don't know.
 *
 * Copyright (c) 2009: Sylvain Joyeux <sylvain.joyeux@m4x.org>
 */
#include <acpi/acpi.h>

MODULE_LICENSE("GPL");

static acpi_handle root_handle;

static int __init kill_ati(void)
{
    int i;
    acpi_status status;
    // The device handle
    acpi_handle handle;
    // The package elements
    union acpi_object package_elements[3];
    // The arguments to ATPX
    union acpi_object atpx_arg_elements[2];
    struct acpi_object_list atpx_arg;
    // For the return value of ATPX
    struct acpi_buffer buffer = { ACPI_ALLOCATE_BUFFER, NULL };

    status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.ATPX", &handle);
    if (ACPI_FAILURE(status))
    {
        status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.XTPX", &handle);
        if (ACPI_FAILURE(status))
        {
            printk("lenovo_acpi: cannot get ACPI handle: %s\n", acpi_format_exception(status));
            return -ENOSYS;
        }
        printk("lenovo_acpi: in discrete graphics mode\n");
        return 0;
    }

    for (i = 0; i < 3; ++i)
    {
        package_elements[i].type = ACPI_TYPE_INTEGER;
        package_elements[i].integer.value = 0;
    }

    atpx_arg.count = 2;
    atpx_arg.pointer = &atpx_arg_elements[0];

    atpx_arg_elements[0].type = ACPI_TYPE_INTEGER;
    atpx_arg_elements[0].integer.value = 2;

    atpx_arg_elements[1].type = ACPI_TYPE_PACKAGE;
    atpx_arg_elements[1].package.count = 3;
    atpx_arg_elements[1].package.elements = &package_elements[0];
    
    status = acpi_evaluate_object(handle, NULL, &atpx_arg, &buffer);
    if (ACPI_FAILURE(status))
    {
        printk("lenovo_acpi: ATPX method call failed: %s\n", acpi_format_exception(status));
        return -ENOSYS;
    }
    kfree(buffer.pointer);

    printk("lenovo_acpi: disabled the discrete graphics card\n");
    return 0;
}

static void dummy(void)
{
}

module_init(kill_ati);
module_exit(dummy);
```i am using Ubuntu 12.04 beta 2

Eagrly wating for reply guys..

Look, I never used something like this before, but I'm used to use # echo OFF > /sys/kernel/debug/vgaswitcheroo/switch which stops the discrete graphic card in my case.

To make it run in boot, just do this:

```
sudo gedit /etc/init.d/vgabootup.sh
```

Then type in there:

```
#!/bin/bash

echo "OFF" > /sys/kernel/debug/vgaswitcheroo/switch

```

After this, you need to make it executable and link in rc0.d, to make it run in boot.

```
chmod +x /etc/init.d/vgabootup.sh
sudo update-rc.d vgabootup.sh defaults
```

Hope it works for you.

---

