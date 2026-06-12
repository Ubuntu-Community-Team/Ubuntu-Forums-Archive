---
title: "grub/splash/usplash --help?"
date: 2007-03-31
forum: Desktop Effects &amp; Customization
---

### Post by Simimi on 2007-03-31
So, I was originally trying to add an image to the grub splash screen, which led to trying to change the uSplash, which led to me not having a usplash, or a gnome splash screen. I've have searched around for a few fixes or a way to reset the system back to default Edgy settings, but I have not found anything that has worked (which is odd, because everything I have tried has looked like it should work, all things considered...)

I now have a handful of tiny problems, I'm hoping you all can help me figure out... once they are solved we could always clean the answer up and add it to the ubuntu wiki!

So, in giving up trying to fix the problem, I have decided to try and remedy it instead. I am trying to install the uSplash theme from [THIS LINK]("http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468")
 I follwed the readme instructions and it now works (I have a uSplash now). The problem is, in my /boot/grub/menu.lst grub was set to quiet, so I removed the quiet flags. Now, when my system boots, the textbox from the boot being non-quiet, falls below the box from the theme. and it is intrusive and looks like a back box was pasted on top of the usplash window. Enter Problem 1...

1) If you look at the image of the usplash from the above link, it is supposed to have something in the default box in the usplash screen (looks like a double helix) I thought the text from a non-quiet boot was to go in there, can anyone think of a way to put it in there? OR, is there a way to get it so it looks as it should from the links on Gnome-Look? (It reads, "Press alt+F1 for verbose mode" and "Now loading LINUX... the most advanced operating system in the world.") On mine, it simply has a blackened box where the double-helix and the above mentioned text should be... I am somewhat out of ideas.

2) I think I just solved the second problem, which, kinda makes me feel dumb. I downloaded an image for the grub loader, from kde-look.org to use on Gnome... which should not matter since it is the grub loader itself, and nothing to do with gnome or kde, right? Therefore, I have not solved the second problem at all!

Well, the image/file can be found [THIS LINK]("http://www.kde-look.org/content/show.php/kde+linux+grub?content=38280").
I followed the given instructions found on that page, and edited the /boot/grub/menu.lst file as it suggests... here is my menu.lst file, for reference...

```

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro splash
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda5 ro splash locale=en_EN vga=791
splashimage=(hd0,1)/boot/grub/splashimages/grub_red.xpm.gz

```

The second kernel line is for the problem 1 image, the splashimage= line is for the problem 2 grub image...
I have a dir in /boot/grub such that...
```

simimi@my-linux-complex:/boot/grub/splashimages$ ls
grub_red.xpm.gz

```
Any suggestions for getting this grub thing to work?

3) Is there a way to save a panel in Gnome? I have something like 7... (different ones for different themes or lang/locale settings) and it would be nice to be able to just load them or something when I need a new one, instead of keeping them on different workspaces. As a related question, can you make a workspace completely different from the main space? So , instead of loging into the user 'China' when I want my Chinese locale and theme and such, it could just default as the second workspace when I log in normally as me?


This is a bit long, but I hope it helps to get these problems taken care of! 
Regards,
 Mimi:confused:

---

