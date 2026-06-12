---
title: "[SOLVED] I can't see Ubuntu!"
date: 2008-07-21
forum: Desktop Environments
---

### Post by simonzippy on 2008-07-21
Hi all, another brand new Ubuntu user here and I've mucked up already!

I was changing settings in Compiz Fusion and I have managed to make every single screen in Ubuntu blank. The last thing I changed was windows reflections, since then I can't get back into it to remove the tick I put in to reverse it cause I can't see where I'm clicking. I can run my mouse over things and I know the settings are there because grey boxes appear where the windows should be.

I am writing this in Vista, which, incidently I noticed how remarkably slow it is to start up.
I like Ubuntu. I see it as a platform which only provides what you need when you start with it, and you can build what you like with it by using addons. This poses a problem for me though cause I have broken it already!

Thanks

Si

---

### Post by Potatoj316 on 2008-07-21
Have you seen this only once, or have you restarted since the problem started and seen it again?

---

### Post by simonzippy on 2008-07-21
Wow that was quick! Everytime. I have restarted numerous times.

---

### Post by damis648 on 2008-07-21
Can you take a screenshot? Press Print Screen on your keyboard and press enter when the new window appears. Then you will see a new file on your desktop. Try plugging in a flash drive, and then just drag that file onto the new desktop item which is the flash drive.

---

### Post by Potatoj316 on 2008-07-21
I know this is possible in the terminal but I just dont know which file is the one you need to edit.

---

### Post by simonzippy on 2008-07-21
I tried to take a screen shot but unfortunately I am unable to see my flash drive to load it on to. Sorry.

---

### Post by damis648 on 2008-07-21
I have a plan. Press alt+f2. When I new window appears, type
```
metacity --replace
``` and press enter.
You should be good temporarily. Start up a terminal (Applications>Accessories>Terminal). In the terminal, type
```
rmdir .compiz
```
and reboot. See what happens.

---

### Post by rogier.de.groot on 2008-07-21
Could you press Ctrl+1 (or Alt+1 I keep forgetting which) and log in to the plain old text mode terminal? You could then remove your whole compiz configuration with the command "rm -rf ~/.config/compiz" which should fix the problem... I think...

---

### Post by damis648 on 2008-07-21
> **rogier.de.groot said:**
> Could you press Ctrl+1 (or Alt+1 I keep forgetting which) and log in to the plain old text mode terminal? You could then remove your whole compiz configuration with the command "rm -rf ~/.config/compiz" which should fix the problem... I think...

It is actually ALT+F1. Other than that, the sounds like a sound plan. After you are done, Type sudo reboot to reboot and you should be OK.

---

### Post by simonzippy on 2008-07-21
Great, I will give it a try. I have to go out but when I get back I'll try it and will let you know straight away if it works.

Thanks guys.

---

### Post by simonzippy on 2008-07-22
Hi, just to let you know that the metacity command worked first time for me.
As soon as I entered it my screen appeared.
I didn't use the rm -rf ~/.config/compiz command as I think I must have set my keyboard up incorrectly during installation as I can't use the "wavey hyphen?" key.

Apart from that I didn't seem to need to do anything else.

I just wanted to say a genuine thanks for your help guys. Really appreciated.
I have a feeling I will be take take take for a very long time until I get the hang of thing sufficiently.

Thanks again.

Si

---

### Post by russo.mic on 2008-07-25
> **simonzippy said:**
> Hi, just to let you know that the metacity command worked first time for me.
As soon as I entered it my screen appeared.
I didn't use the rm -rf ~/.config/compiz command as I think I must have set my keyboard up incorrectly during installation as I can't use the "wavey hyphen?" key.

Apart from that I didn't seem to need to do anything else.

I just wanted to say a genuine thanks for your help guys. Really appreciated.
I have a feeling I will be take take take for a very long time until I get the hang of thing sufficiently.

Thanks again.

Si

Well, the "watery hyphen" key is called the tilda, and it represents your home folder.  so, if your user name is bob, then ~ = /home/bob.  

That having been said, the command you should enter to equal what you want is:

rm -rf /home/"your user name"/.config/compiz

---

### Post by russo.mic on 2008-07-25
> **simonzippy said:**
> Hi, just to let you know that the metacity command worked first time for me.
As soon as I entered it my screen appeared.
I didn't use the rm -rf ~/.config/compiz command as I think I must have set my keyboard up incorrectly during installation as I can't use the "wavey hyphen?" key.

Apart from that I didn't seem to need to do anything else.

I just wanted to say a genuine thanks for your help guys. Really appreciated.
I have a feeling I will be take take take for a very long time until I get the hang of thing sufficiently.

Thanks again.

Si

Well, the "watery hyphen" key is called the tilda, and it represents your home folder.  so, if your user name is bob, then ~ = /home/bob.  

That having been said, the command you should enter to equal what you want is:

rm -rf /home/"your user name"/.config/compiz

Good Luck!

---

