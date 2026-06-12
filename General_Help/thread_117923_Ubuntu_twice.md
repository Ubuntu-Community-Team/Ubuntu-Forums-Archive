---
title: "Ubuntu twice"
date: 2006-01-15
forum: General Help
---

### Post by Red Knuckles on 2006-01-15
Me being a noob but liking Ubuntu very much [9months on Fedora Core 3&4] decided I wanted to check out the KDE Desktop environment. So I installed Kubuntu and all went well except it recognizes my monitor as 640x480 [instead of the preferred 1024x768]. If anyone on this Forum can help me with that I would appreciate it but that is a topic for Kubuntu Forums. My question for this Forum is that when I reboot Ubuntu is listed twice. Perhaps because I did an apparently now unnecessarily reinstall. Is Ubuntu on my HD twice? I used the same username and password and when I boot in either one they are the same. In order to conserve HD space how can I get rid of one of them?:confused:

---

### Post by eyebrowman92 on 2006-01-15
you mean on your grub menu? if so one is probably entered twice?  in your file manager, go to /boot/grub/menu.lst and see if there are two ubuntu entries. if there are delete oe. be careful though...

---

### Post by Mustard on 2006-01-15
It may be two different kernel entries after a kernel update.  This doesn't mean that ubuntu is installed twice.  It would just mean you have two different kernels to choose to boot from.  The old kernel and the updated kernel.

I would look at the numbers a bit more carefully when you boot up next and you might find that one is a 2.6.12-9-386 kernel and the other is a 2.6.12-10-386 kernel.

---

### Post by eyebrowman92 on 2006-01-15
[QUOTE=Mustard]It may be two different kernel entries after a kernel update.  This doesn't mean that ubuntu is installed twice.  It would just mean you have two different kernels to choose to boot from.  The old kernel and the updated kernel.

I would look at the numbers a bit more carefully when you boot up next and you might find that one is a 2.6.12-9-386 kernel and the other is a 2.6.12-10-386 kernel.[/QUOTE]


yes or that. hah

---

### Post by Mustard on 2006-01-15
Yeah, my grub menu has gotten quite extended over time, especially when I have been mucking around installing k7 kernel as well.  It's not a bad thing to have two kernels to boot from either, as if one kernel goes down for whatever reason, you always have the option of booting from the other.

---

### Post by aysiu on 2006-01-15
Can you go to Applications > Accessories > Terminal and then post here the output of this command? ```
cat /boot/grub/menu.lst
```

---

### Post by Red Knuckles on 2006-01-15
[QUOTE=Mustard]It may be two different kernel entries after a kernel update.  This doesn't mean that ubuntu is installed twice.  It would just mean you have two different kernels to choose to boot from.  The old kernel and the updated kernel.

I would look at the numbers a bit more carefully when you boot up next and you might find that one is a 2.6.12-9-386 kernel and the other is a 2.6.12-10-386 kernel.[/QUOTE]

Ok, I'll admit it. Embarrassed Linux and beer. It's 2 kernel entries. In Fedora I'd always keep 2 most recent and delete the oldest one when there was a kernel update.:rolleyes:

---

### Post by aysiu on 2006-01-15
If you want to get rid of the old one, just ```
sudo apt-get remove linux-image-2.6.12-9-386
```

---

### Post by Red Knuckles on 2006-01-15
[QUOTE=aysiu]If you want to get rid of the old one, just ```
sudo apt-get remove linux-image-2.6.12-9-386
```[/QUOTE]

In Fedora you could also do that in Synaptic. I assume it would be the same in Ubuntu.:)

---

### Post by aysiu on 2006-01-15
[QUOTE=Red Knuckles]In Fedora you could also do that in Synaptic. I assume it would be the same in Ubuntu.:)[/QUOTE] Yes, you can do it in Synaptic. It's just easier for me to give you the terminal command.

---

### Post by Red Knuckles on 2006-01-15
[QUOTE=Red Knuckles]In Fedora you could also do that in Synaptic. I assume it would be the same in Ubuntu.:)[/QUOTE]

Ok, I just checked and it doesn't appear there in the way I'm used to so I thank you very much for the tip!:)

---

### Post by aysiu on 2006-01-15
[QUOTE=Red Knuckles]Ok, I just checked and it doesn't appear there in the way I'm used to[/QUOTE] So it doesn't appear like this?

---

### Post by Red Knuckles on 2006-01-15
[QUOTE=aysiu]So it doesn't appear like this?[/QUOTE]

Actually it does. It's just listed differently than in Fedora. Thanks, you've been a big help.:)

---

### Post by morphodone on 2006-01-15
[QUOTE=Red Knuckles]So I installed Kubuntu and all went well except it recognizes my monitor as 640x480 [instead of the preferred 1024x768].[/QUOTE]


Doesn't seem like anyone answered this yet...
open a console and

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg

that should give an option to select your monitor type
and resolution.

---

### Post by Red Knuckles on 2006-01-15
[QUOTE=Red Knuckles]Actually it does. It's just listed differently than in Fedora. Thanks, you've been a big help.:)[/QUOTE]

For what it's worth in Fedora the kernel versions are listed in Synaptic as:

kernel-2.whatever.

---

### Post by Red Knuckles on 2006-01-15
[QUOTE=morphodone]Doesn't seem like anyone answered this yet...
open a console and

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg

that should give an option to select your monitor type
and resolution.[/QUOTE]

Hey, thanks. I'm going to reboot and try that right now. This Forum ROCKS. I've gotten nothing from the Kubuntu Forum yet. Guessing it's a smaller group.:)

---

### Post by Red Knuckles on 2006-01-15
[QUOTE=morphodone]Doesn't seem like anyone answered this yet...
open a console and

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg

that should give an option to select your monitor type
and resolution.[/QUOTE]

That didn't work. I went thru a lengthy dialog and was able to set monitor resolution to 1024X768. When I rebooted it entered Kubuntu and started the 'Loading Modules' but then it goes to a text screen which stopped at 'checking battery status'. What did I do wrong?:confused: :confused:

---

### Post by Red Knuckles on 2006-01-15
[QUOTE=Red Knuckles]That didn't work. I went thru a lengthy dialog and was able to set monitor resolution to 1024X768. When I rebooted it entered Kubuntu and started the 'Loading Modules' but then it goes to a text screen which stopped at 'checking battery status'. What did I do wrong?:confused: :confused:[/QUOTE]

One thing I remember is that my graphics card is an Intel I810. The gui asked me to select it's memory. None was listed and it stated that one could proceed with none selected. I hit OK. Maybe I should have selected 0? How do I undo this?:confused:

---

### Post by aysiu on 2006-01-15
Something [here](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) has got to help.

---

### Post by morphodone on 2006-01-15
[QUOTE=Red Knuckles]One thing I remember is that my graphics card is an Intel I810. The gui asked me to select it's memory. None was listed and it stated that one could proceed with none selected. I hit OK. Maybe I should have selected 0? How do I undo this?:confused:[/QUOTE]

Changing xorg.conf should not prohibit ubuntu from booting...it would boot but maybe not to a gui.  I've torched my xorg.conf many times but it always leads me to a console login.  From there I could always fix the problem.  Try hitting 
all at the same time:   Ctrl + Alt + F1

If you made the backup you can simply copy it back over...if you get to a login screen.  

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

---

