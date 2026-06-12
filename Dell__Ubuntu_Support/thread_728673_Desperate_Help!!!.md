---
title: "Desperate Help!!!"
date: 2008-03-19
forum: Dell  Ubuntu Support
---

### Post by WalkerM on 2008-03-19
Okay heres my situation,

I have a Dell 1521 laptop and I installed Ubuntu 7.10 about a week ago and dual booted it with Vista. Up till tongiht everything has been goin about perfect. The main things I have been doing have been just customizing the Appearence to my liking and getting the wireless to work. I got the wireless to work but for some reason my touchpad settings were reset and the tap click was enabled (I disabled tapping 2 days ago) so I went to System>Preferences>Mouse but the Touchpad tab for some reason wasnt there anymore. So I looked for a good amount of time trying to find a solution and I finally decided to go with editing the xorg.conf file to make it so that I could just disable the tapping. I opened the file and added a couple of Options and then I saved it and rebooted so the changes would take affect. It reboots and goes to the Grub loader like it always does and I choose Ubuntu 7.10 generic, but right after I select Ubuntu it looks like it starts to load up to the login screen but the screen goes black and thats it. Everytime it just goes black and sits there, I can't even get into the log in screen or anything. I can still boot into vista perfectly but not even close to Ubuntu. I've literally been looking and searching and trying different ways to solve this for going on 4 hours. I would really like to keep all my settings and personal files if thats at all possible and somehow repair Ubuntu. I do have access to Ubuntu Memtest and Recovery (which is a command prompt). Thank you SO much for whoever helps me!!!!!! I have no idea what to do anymore!!!

---

### Post by Kiri on 2008-03-19
Can you boot into the safe mode? or get to a terminal screen?
Hopefully you just need to change whatever you changed in xorg back again...

---

### Post by oskar-swe on 2008-03-19
Yeah, try to change your xorg.conf back. If that doesnt work, you can just reconfigure your xserver:

(automatically)

$ dpkg-reconfigure -pHIGH xserver-xorg

(manually)

$ dpkg-reconfigure xserver-xorg

Also, ALWAYS make a current back-up of your xorg before editing.

---

### Post by WalkerM on 2008-03-19
alright thanks guys for the help,

I can't even enter Ubuntu but I can get into a Terminal screen so I entered: dpkg-reconfigure -pHIGH xserver-xorg

I went through all the questions and now I'm on the question about how many bits I am running at, I selected 24 (+8 for alpha channel) and at the bottom of the screen a command line popped up blank, what do I do now?

again thanks for the help!

---

### Post by Kiri on 2008-03-19
Try typing:

/etc/init.d/gdm start

---

### Post by WalkerM on 2008-03-19
okay I entered

```
/etc/init.d/gdm start
```

and  I got this message:

> * Starting GNOME Display Manager....                               [ OK ]


and then another blank command line

---

### Post by MONODA on 2008-03-19
try:
```
startx
```
then:
> /etc/init.d/gdm start

---

### Post by WalkerM on 2008-03-19
I entered startx and it ran a quick log or scan then I entered the second code /etc/.... and it did the same thing

---

### Post by WalkerM on 2008-03-19
When I try to boot normally with Ubuntu I get this message for a split second b4 it freezes

Cannot allocate resource region 5.... something like that


Does that tell you guys anything?

---

### Post by Zeedok on 2008-03-20
This is really chickening out but when I have really stuffed things up in the part I have just booted the live cd and either copied the files I have stuffed up with the default ones from the cd, or simply reinstalled the whole os. I have also partitioned my hd to include a drive which is accessible from vista and ubuntu for all my files, templates etc. Then if you have to reinstall or whatever, you still have your files etc. You can even point oo to the same folders for autocorrect and so on.

hope you find this useful

---

### Post by oskar-swe on 2008-03-20
That shouldn't be your problem. I think. have a look at :[http://ubuntuforums.org/showthread.php?t=265132]("http://ubuntuforums.org/showthread.php?t=265132")

Also, did you do the commands as root (or sudo)? It's important.

Also im not sure about the -pHIGH, maybe it should be in lowercase (or maybe it's not important), so your command would be:

$ sudo dpkg-reconfigure -phigh xserver-xorg

---

