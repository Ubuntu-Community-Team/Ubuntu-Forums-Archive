---
title: "I love Ubuntu but something whent wrong please help!"
date: 2009-02-28
forum: General Help
---

### Post by 220010497 on 2009-02-28
Well, i have an issue, i'm posteing this from the live boot CD becase, well last night i get really intrested in programs for my ubuntu and i got a whole bunch of them... but when i rebooted, i get the normal screen but then...black... then i get the commands of what loads ubuntu and then i got: 

Joining cluster:cman_tool: Corosync died during startup

fence_tool: waiting for cman to start

ccs [4283]: CCS ] Unable to connect to cluster infastructure after 90 seconds.

----------------------

It repeats the second line i wrote and nothing happens, then i tryed the boot CD and well what do i find..... my boot CD has no recover function... 

so please some one from ubuntu forums or some where help me. i love my computer and i'm a student that needs his computer working, i use to have Windows XP, but i trashed it becase it would not let me use what i needed and i dident want to pay 200$ for a vista disc.

i looked throuh forums and i couldent find anything that matches my topic, all of my work is on here, my files, pictures, music, books, storys, journals, Videos of when me and my mate adopted and yes..ima guy and im with another guy..dont disciminate,......... and pictures of uncles funaral and me and my mates wedding on here i need but i cant get to them and if i lose them i will go emotionally insane. 

My mate Richard tryed to fix it but he said he cant becase he dosent understand what it is talking about....:lolflag: and i thought my computer nerd husband could help...:tongue:

Please help me,

Love: 220010497 aka :KS Cody :KS.  add me to live messenger if you like at [email]killpup@hotmail.com[/email]    its on my mobile.

---

### Post by emarkay on 2009-02-28
This is when you boot from the Live CD?

Did you "test CD for Defects"?

Or is this normal booting that is not working but the Live CD is OK?

If it's the latter, than first make sure you have not just rebooted, but turned off the PC power, then reboot.

Id you still get that error can you get into the "recovery console"?

---

### Post by emarkay on 2009-02-28
This has something to do with the IP tables:

[http://www.mail-archive.com/linux-cluster@redhat.com/msg04737.html](http://www.mail-archive.com/linux-cluster@redhat.com/msg04737.html)

Have you done any customizations - what type of PC?

---

### Post by 220010497 on 2009-03-01
> **emarkay said:**
> This has something to do with the IP tables:

[http://www.mail-archive.com/linux-cluster@redhat.com/msg04737.html](http://www.mail-archive.com/linux-cluster@redhat.com/msg04737.html)

Have you done any customizations - what type of PC?



i've fixed my problem,   when the command for:  fence_tool: waiting for cman to start...     
just push ctrl+alt+delete.   and then you get to your log in screen, once you log in open the termanal and put in:  sudo apt-get remove cman libfence3

And thats all there is too it, hope it helps some one, i know it fixed me issue

---

### Post by Jim.uff on 2009-03-08
Thanks, I had the same problem and this worked for me too. Another error message I noticed just before it hung had a red asterik and said 'system does not have CPU extensions for KVM'. I don't know for sure but suspect they are related. I also removed the KVM files. Don't think I really loaded those in but some where they may have gotten included in my ongoing efforts to get sound.

---

### Post by linuxisevolution on 2009-03-08
You should be able to boot from the live cd and copy your old files from your hard drive to something like and external hard drive or flash drive to another computer..

---

### Post by hyper_ch on 2009-03-08
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read

---

### Post by spike_naples on 2009-03-24
Thank you. I tried it in terminal as I am still able to boot into Ubuntu. Somethings were removed and hopefully something will work well after this. If I don't reply after this then it would mean that everything is fine.

God bless all the contributors!

---

### Post by spike_naples on 2009-03-24
> **220010497 said:**
> i've fixed my problem,   when the command for:  fence_tool: waiting for cman to start...     
just push ctrl+alt+delete.   and then you get to your log in screen, once you log in open the termanal and put in:  sudo apt-get remove cman libfence3

And thats all there is too it, hope it helps some one, i know it fixed me issue

I didn't want to reply as it obviously worked but thanks to you, in less than 5 mintues after typing it into the terminal I rebooted and never got those pesky errors.

Thanks so much again.

---

### Post by emoXodus on 2009-04-05
i have the same problem hopefully the code will work

---

