---
title: "uninstall single boot"
date: 2009-06-03
forum: General Help
---

### Post by blastbar on 2009-06-03
hi i want to clear my computer of OS's so i can start again fresh, i dont have any other disks like windows or mac and dont want to create, and havent already got, a dual booting system.  Is there a way i can uninstall ubuntu without filling the space with another OS?
  I've looked into it and can't find info on the internet or in this forum    any help much appreciated =]  ps. ubuntu desktop edition 9.04      thanks

---

### Post by mmarif4u on 2009-06-03
Can you explain this a bit?
> Is there a way i can uninstall ubuntu without filling the space with another OS?

Does you mean:
You have 9.04 now and want a clean install?

---

### Post by blastbar on 2009-06-03
sorry for being so vague, I mean can i erase the OS from my drive so my computer effectively has nothing on it?

---

### Post by Pooven on 2009-06-03
Hi there :)

Perhaps I've misunderstood, but the simplest way that comes to mind is to just quick format the hard drive.

So I would:
[LIST=1]
[*]Boot using the LiveCD
[*]Start gparted via the menu: System > Administration > Partition Editor
[*]You should be able to see your hard drive and/or partitions that exist on it: right click on the partition you want to format and you'll notice the option *Format to*.
[/LIST]

Choose the appropriate file system you want from the *Format to* menu and once you click *Apply*, you'll have an empty hard drive. You can also choose to delete a partition in which case there will be no file system at all. 

Of course, when you install Ubuntu, *gparted* automatically pops up during installation in which case you could format and/or delete partitions as described here (if you choose to manually set up the partitions).

---

### Post by blastbar on 2009-06-03
thank you so so much i'll try this out now n see if i can master it =]

---

### Post by Pooven on 2009-06-03
You're most welcome - if you get stuck, take a screen shot and post it here so we could advise better... afterall, picture is worth a thousand words :D

---

### Post by blastbar on 2009-06-03
thank you so much, deleted my system of all nonsense, but, (there's always one =p)  i go to re-install from the disk and i go through all the options and everything and then when it says your computer needs to be restarted i click ok and the screen goes black but my computer stays on until i press enter on the keyboard so i'm not sure what it is thats happening if you can help i would be so grateful, as my mouse still hasn't appeared =[

---

### Post by Pooven on 2009-06-03
Oh dear, that does sound bad... though I'm not really sure what you're experiencing. You obviously have installed some version of Ubuntu before hey?

When the setup completes, it usually prompts you to remove the disc from the drive and press enter when ready -- sometimes it doesn't actually restart the computer and you'll have to do it yourself > and I'm quite sure that it's safe to do so. So either switch the computer off and back on or hit the reset button :)

If you did restart and are not able to boot again - my first question would be: Do you see at least see the Grub menu?

---

### Post by blastbar on 2009-06-03
ahhh thank you, i see the grub menu and can reboot fine, i was just concerned i was missing something as other people i know said after putting in the info first time and rebooting, they had to put more info in as though you needed to "install" the disk and then the actual system, but that might just be there machines i don't know

---

### Post by Pooven on 2009-06-03
Ah so I take it all is now well? Great stuff! Hmm, I wonder - perhaps you should mark this thread as solved? I think there's an option to do so... not too sure hehe. Anyway, Happy Ubuntu days :D

---

### Post by blastbar on 2009-06-03
thank you so much for your help and time i really appreciate the quick responses and answers to problems =]

---

### Post by Pooven on 2009-06-03
It was my pleasure! It was almost like a real time chat hey? hehe almost! Anyway, I'm just glad that I was able to assist. Peace :)

---

