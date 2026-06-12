---
title: "Display troubles on a Toshiba Satellite"
date: 2013-02-18
forum: Desktop Environments
---

### Post by Yalio on 2013-02-18
Hi everybody,
I have a "little" problem with an old Toshiba Satellite on that I've recently installed Lubuntu (12.04): there is no way to use the GUI correctly. At startup, when loading, the screen flashes with a lateral shift of the image. Next, a black screen occurs instead of the GUI.

If I go into text mode (*Ctrl + Alt + F1*), the display works. By connecting a VGA output on the screen, I can get better results : the GUI is visible... but again, there are continual flashes (in this case, also in text mode)...
I changed the resolutions and refresh frequencies several times, but it doesn't fix the problem. I also looked at the "additional drivers" module. It seeks about ten seconds then told me that there is no proprietary driver on the machine.

I looked on the Toshiba website, I didn't find any drivers for my own model. Before Lubuntu, Windows XP was installed on that computer and there were no graphical problems.
I nosed too on the (french) ubuntu wiki, and I found a few tracks, but now I'm a bit blocked...

I tried the following command which is supposed to print some informations about my graphical device...
> $ lspci -vnn | egrep "VGA|3D|Display"
00:02.0 VGA compatible controller [0300]: Intel Corporation 82830 CGC [Chipset Graphics Controller] [8086:3577] (rev 04) (prog-if 00 [VGA controller])
00:02.1 Display controller [0380]: Intel Corporation 82830 CGC [Chipset Graphics Controller] [8086:3577]

I looked too about the Xorg config. The /etc/X11/xorg.conf file didn't exist, so I created it. Now, I confess it, I'm a little lost about the way to fill it, despite of the [documentation page]("http://doc.ubuntu-fr.org/xorg") I found (in french).

Finally, I looked at the *xrandr* command. When I called, it returns me a pretty (or it is ?) "*Can't open display*", while the built-in laptop screen actually works.

Does anyone know how to fix the problem?

Thanks a lot ! :P



[SIZE="1"]P.S : I'm French a I have translated this post from an original one, written in french which doesn't received any answers.
So I apologize for the grammar mistakes which can appears in the post here.[/SIZE]

---

### Post by oldfred on 2013-02-18
Welcome to the forums.

I have an even older Toshiba with Intel graphics. Mine just works. 
But Intel has only one driver and it is the standard open source driver installed. 

Some have needed extra parameters.
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
Older Intel video card: i915.modeset=1 or i915.modeset=0 
newer:  i915.i915_enable_rc6=1 

Force Intel Video mode as boot parameter in grub menu (change example to your sizes)
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

   For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

  For Intel 945g info to show the graphic card properly,install mesa-utils package from USC (software center).

Usually it is only the very new Intel chips that need extra parameters or the very newest Intel driver which Intel is regularly updating.

---

### Post by Yalio on 2013-02-18
Thanks for responding.

I tried all the ways you have suggested. There is the results :

[LIST]
[*]***Add *i915.modeset=1* in the /etc/default/grub config file*** : it seems that the shift is gone after I done that.
The screen continue to flashs, yet ;
[*]***Installing mesa-utils*** : when I calls *glxinfo* from a "tty" terminal, it prints "No screen found" (or something like that)...
[*]***Adding "video=1280x1024-24@60".*** I don't know how I can save the file after editing it. I do Ctrl + S, but the file is reseted after each reboot. Is it normal ?
The first time I done "Ctrl + S" before press F10 [SIZE="2"](it is the first time I use Emacs)[/SIZE], a weird windows was appeared asking me about the kind of boot I wanted to do. I chose the "resume" entry, then the GUI occurs without any flash.
[/LIST]
Since this trial, I can't obtain the same result. :confused:

---

### Post by oldfred on 2013-02-18
I do not know what else to try. Hopefully someone else with a similar Intel chip will come along and help.

All the boot options I would try with the e on grub menu and see it they work first before changing grub or making permanent.

---

### Post by Yalio on 2013-02-19
I did a new test this evening with the second option you suggested.
When I have submited my grub config changes in GRUB by doing Ctrl + X (not F10 and without doing Ctrl + S before, I don't know if that can change something to the computer behavior), the grub windows appeared asking me about what I want to do (I believe it was a recuperation mode).

When selection the "Resume" entry, the GUI appeared, exactly like it happened with the first option.
...And exactly like the first option, since this trial, I'm unable to obtain the same result.

I believe that I will reinstall W$...

---

