---
title: "How to Start Full X Session...?"
date: 2009-02-09
forum: Desktop Environments
---

### Post by packet123 on 2009-02-09
Hello All,

I am Using Kubuntu...(kubuntu8.10 from pendrivelinux.com ) I am booting Kubuntu from the 2 gb Pen drive 
and in the starting it will give a 12 different options to boot .

Like as follows
                                ADRIANE

1 Press Enter for a help 
2
3
4
5
6
7
8
9
10
11
12

in the 10 th option there is a full x session ...

**My question is How to skip all these steps and to start full x session without any entering from the keyboard option ?**

Is thgis possible to boot directly to X session ?
is there any files to add or to edit in the booting ?
If yes please guide me in steps ?

thanks

---

### Post by adamlau on 2009-02-09
Not sure how the pendrive works, but you typically (if no xdm/gdm/kdm) add the following to your ~/.bash_profile

```
if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/vc/1 ]]; then
  startx
  logout
fi
```

And the following to your ~/.xinitrc

```
exec startkde
```

---

### Post by kerry_s on 2009-02-09
> if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/vc/1 ]]; then
  startx
  logout
fi

that's for arch, the *buntu's use tty:

```
if [[ -z "$DISPLAY" ]] && [[ $(tty) = **/dev/tty1** ]]; then
  startx
  logout
fi
```

> My question is How to skip all these steps and to start full x session without any entering from the keyboard option ?


those look like boot options, do you know what boot loader it uses?
look in /boot

---

### Post by packet123 on 2009-02-09
Hi,

Its simple thing to boot from pendrive follow the instructions from this link you will get a pend drive kubuntu linux ....
[URL="http://www.pendrivelinux.com/usb-kubuntu-810-persistent-install-using-windows/"]http://www.pendrivelinux.com/usb-kubuntu-810-persistent-install-using-windows/
[/URL]
It has boot loader syslinux.cfg ... what i need to change in that ?

Is there any option to put my script that will run Before the boot or after the boot ? (Note : please go through one of my Thread Another solution..!!!)

---

