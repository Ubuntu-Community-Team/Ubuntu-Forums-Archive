---
title: "Help me file a bug report!"
date: 2011-06-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jetro on 2011-06-01
In order for the bug to be looked at, one has to do it properly.

I'm having brightness adjusting issues with my Inspiron 9400 since 10.10.
I have created a noobish [bug report](https://bugs.launchpad.net/ubuntu/+bug/790435), and was asked to follow [this](https://wiki.ubuntu.com/Kernel/Debugging/Backlight) to create an accurate history.

I have done the first few steps, namely adding **acpi_backlight=vendor** to the kernel boot parameters and updated Grub. That actually resolved the issue somehow, but I suppose more is needed to describe the problem.


_[SIZE="3"]***Things to do:***[/SIZE]_
[LIST=1]
[*]Disabling the ACPI backlight driver
 [SIZE="3"][COLOR="#006400"]**Done.** This almost resolved the issue (still sometimes buggy, but much better than before).[/COLOR][/SIZE]

[*][s]Check to see if your system uses the thinkpad-acpi driver by using the following command: **lsmod | grep thinkpad_acpi**[/s]  
 [SIZE="3"][COLOR="DarkRed"]**No result**, no need.[/COLOR][/SIZE]

[*]Checking the kernel interfaces:
 
[LIST]
[*][FONT="Courier New"]ls /proc/acpi/video/
[COLOR="DarkRed"]**ls: cannot access /proc/acpi/video/: No such file or directory**[/COLOR][/FONT]

[*][FONT="Courier New"]ls /sys/class/backlight/
[COLOR="DarkGreen"]**dell_backlight**[/COLOR][/FONT]
[/LIST]

[*]Into the abyss: looking at the ACPI BIOS

[/LIST]

Any help is greatly appreciated :)

---

### Post by Mariane on 2011-06-02
> **Jetro said:**
> 
Check to see if your system uses the thinkpad-acpi driver by using the following command: **lsmod | grep thinkpad_acpi** (I ran this, with no results)


I think no results means your system is not using it. For the rest I don't know. 

Mariane

---

### Post by mikewhatever on 2011-06-02
- According to the wiki, adding acpi_backlight=vendor disables the ACPI backlight driver.

- Inspiron 9400 is a Dell, right? [Thinkpad]("https://secure.wikimedia.org/wikipedia/en/wiki/ThinkPad") is a formerly IBM and now Lenovo line of notebooks. I doubt you should be using a Thinkpad acpi driver on a Dell, so skip that step.

- To start with the kernel interfaces, run the following:
```
ls /proc/acpi/video/

ls /sys/class/backlight/
```

- I hope you won't have to go into ACPI BIOS. :P

---

### Post by Jetro on 2011-06-07
Hello and thanks for your replies. :)

mikewhatever: The first command gave me this message: 
[FONT="Courier New"]ls /proc/acpi/video/
ls: cannot access /proc/acpi/video/: No such file or directory[/FONT]

The second one: 
[FONT="Courier New"]ls /sys/class/backlight/
dell_backlight[/FONT]

Removed [FONT="Courier New"]acpi_backlight=vendor[/FONT], updated Grub and rebooted. Ubuntu started just as normally, no differences that I can see, and back to scratch: Brightness jumping from no light to full light in no time at all, impossible to slightly adjust it.

Also, the fourth step looks sort of dangerous, if I read you correctly, you don't want me to do it, right? :p

I have also updated the first post ;)

---

