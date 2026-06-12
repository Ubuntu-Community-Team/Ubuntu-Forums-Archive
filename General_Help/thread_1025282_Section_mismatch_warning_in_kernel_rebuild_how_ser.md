---
title: "Section mismatch warning in kernel rebuild: how serious is it?"
date: 2008-12-29
forum: General Help
---

### Post by wirawan0 on 2008-12-29
I own a Dell laptop which suffers from a woe of [bug #285323]("https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/285323"). The workaround was very simple but it required kernel rebuild. I downloaded 2.6.27-10.20 source from Ubuntu archive and configured it based on the Ubuntu's settings (/boot/config-2.6.27-10-generic). But I decided to strip down many more modules and some features that I already deem not relevant for my laptop. I followed the procedure given in [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) . Here's where the thing gets more interesting.

I got a warning like this:

```

WARNING: modpost: Found 9 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'

```

re-making with the CONFIG_DEBUG_SECTION_MISMATCH=y switch gives:

```

  LD      init/built-in.o
WARNING: init/built-in.o(.text+0x5d6): Section mismatch in reference from the function acpi_find_dsdt_initrd() to the variable .init.data:file_mem
The function acpi_find_dsdt_initrd() references
the variable __initdata file_mem.
This is often because acpi_find_dsdt_initrd lacks a __initdata 
annotation or the annotation of file_mem is wrong.

WARNING: init/built-in.o(.text+0x5e6): Section mismatch in reference from the function acpi_find_dsdt_initrd() to the variable .init.data:file_looked_for
The function acpi_find_dsdt_initrd() references
the variable __initdata file_looked_for.
This is often because acpi_find_dsdt_initrd lacks a __initdata 
annotation or the annotation of file_looked_for is wrong.

WARNING: init/built-in.o(.text+0x5ed): Section mismatch in reference from the function acpi_find_dsdt_initrd() to the function .init.text:unpack_to_rootfs()
The function acpi_find_dsdt_initrd() references
the function __init unpack_to_rootfs().
This is often because acpi_find_dsdt_initrd lacks a __init 
annotation or the annotation of unpack_to_rootfs is wrong.

WARNING: init/built-in.o(.text+0x5f5): Section mismatch in reference from the function acpi_find_dsdt_initrd() to the variable .init.data:file_looked_for
The function acpi_find_dsdt_initrd() references
the variable __initdata file_looked_for.
This is often because acpi_find_dsdt_initrd lacks a __initdata 
annotation or the annotation of file_looked_for is wrong.

WARNING: init/built-in.o(.text+0x601): Section mismatch in reference from the function acpi_find_dsdt_initrd() to the variable .init.data:file_mem
The function acpi_find_dsdt_initrd() references
the variable __initdata file_mem.
This is often because acpi_find_dsdt_initrd lacks a __initdata 
annotation or the annotation of file_mem is wrong.

WARNING: init/built-in.o(.text+0x60a): Section mismatch in reference from the function acpi_find_dsdt_initrd() to the variable .init.data:file_mem
The function acpi_find_dsdt_initrd() references
the variable __initdata file_mem.
This is often because acpi_find_dsdt_initrd lacks a __initdata 
annotation or the annotation of file_mem is wrong.

WARNING: init/built-in.o(.text+0x615): Section mismatch in reference from the function acpi_find_dsdt_initrd() to the variable .init.data:file_mem
The function acpi_find_dsdt_initrd() references
the variable __initdata file_mem.
This is often because acpi_find_dsdt_initrd lacks a __initdata 
annotation or the annotation of file_mem is wrong.

```

and two others. How serious are these warnings, actually? Would they cause my kernel to be improperly built? I am operating this kernel right now, and it seems to be doing OK. I wonder if this has to do with my tweaking of the .config file (but I think if something is improper, the build process should have caught it).

Wirawan

---

### Post by dcstar on 2008-12-30
> **wirawan0 said:**
> I own a Dell laptop which suffers from a woe of [bug #285323]("https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/285323"). The workaround was very simple but it required kernel rebuild. I downloaded 2.6.27-10.20 source from Ubuntu archive and configured it based on the Ubuntu's settings (/boot/config-2.6.27-10-generic). But I decided to strip down many more modules and some features that I already deem not relevant for my laptop. I followed the procedure given in [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) . Here's where the thing gets more interesting.

I got a warning like this:
......

You would be better to ask this in a kernel development/programming forum, it is far to specialised to get a definitive answer in a forum like this.

---

