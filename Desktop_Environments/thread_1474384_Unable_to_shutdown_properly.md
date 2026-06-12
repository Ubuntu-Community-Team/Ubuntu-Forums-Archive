---
title: "Unable to shutdown properly"
date: 2010-05-06
forum: Desktop Environments
---

### Post by mandeep_mohit on 2010-05-06
Hello Everyone,

I am new Ubuntu user just installed Ububtu 9.10 and I am unable to shutdown properly after choosing Shutdown from the menu it logs off and then I get an error in black screen "[SIZE=4][COLOR=Red]System Halted[/COLOR][/SIZE]" and I wait their but nothing happens. :cry:

Then with no option left I have to switch off my machine to make it shutdown.

Is this normal for Ubuntu, please help.

I don't have such problem with win XP, tried checking other posts similar to this but unable to find a solution.


Thanks & Regards,
Mandeep Mohit.

---

### Post by utnubuuser on 2010-05-06
No, that's un-normal.

This particular issue is something new because a new component called Plymouth has been added to replace xsplash.

I'd try  searching the forum for "plymouth problems". ... I'll see if I can find a link for ya....> [http://ubuntuforums.org/showthread.php?t=1469501&highlight=shutdown+problems+lucid]("http://ubuntuforums.org/showthread.php?t=1469501&highlight=shutdown+problems+lucid")

As a temporary measure, you could try switching to a console from your desktop, Ctrl+Alt+F2, login, then type: > sudo /etc/init.d/gdm stop then type: > sudo shutdown now or > sudo rebootor > sudo shudown -r 0-r is for restart, 0 for -in zero seconds  or > sudo halt to shutdown or restart the system.

AS I've said, it seems to be a relatively common issue, and you might find some info at launchpad too:> [https://launchpad.net/+search?field.text=plymouth]("https://launchpad.net/+search?field.text=plymouth")
and reported bugs concerning this problem:> [https://launchpad.net/+search?field.text=bugs+lucid+shutdown&field.actions.search=Search]("https://launchpad.net/+search?field.text=bugs+lucid+shutdown&field.actions.search=Search")

You might also want to post the output of > lspci -nn so people can see what kind of hardware you're running.

I'd also be inclined to try reinstalling package gdm and/or package plymouth through Synaptic or the command-line.

---

### Post by nitstorm on 2010-05-06
Or you could type 
```

sudo shutdown -P now

```in the terminal to power down the system instantly

Or if you don't like going to the terminal every single time, you could create a Launcher and put this command into it.

But ofcourse, these are just alternatives, better look into utnubuuser's post about the plymouth thing.

---

### Post by mandeep_mohit on 2010-05-07
Thanks a lot for replying I created a Lauchpad with that command however my problem remains the same it just works as a shutdown button and then I get a black screen like dos prompt and nothing happens, then I have to coldboot.

I have P IV 1.5 GHz
Ram 512 MB
Motherboard Intell 816 chipset 
Widows XP installed dual boot
FAT32 both drives
HD - 40 GB

ya i know its quiet an ancient system, I am happy with it I can do my basics with it.

---

