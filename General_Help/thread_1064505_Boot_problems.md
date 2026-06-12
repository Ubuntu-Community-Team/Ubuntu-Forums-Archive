---
title: "Boot problems"
date: 2009-02-08
forum: General Help
---

### Post by racie on 2009-02-08
Okay... so I had this massive error with Xubuntu some time ago, in which it failed to even bring me to the login screen at startup.  The good news was that I had Vista dual-booted with it so I could still use my computer.  So, of course, I was going to uninstall Xubuntu.  When I did, I forgot to shut off my firewall, and it freaked on me.  I shut it off and re-uninstalled it.  Now, my problem is, when my computer boots, I still have the option to pick between Vista and Xubuntu.  I wouldn't dare pick Xubuntu because I have no idea what would happen, but is there any way to take Xubuntu off of the boot screen?  Currently I have Ubuntu and Vista dual-booting, so I have three options at boot, if that means anything.  Thanks for looking at this.

---

### Post by empthollow on 2009-02-08
i assume you are using grub as it is default in xubuntu.  edit the /boot/grub/menu.lst file on you xubuntu partition and remove the entry for xubuntu.  if you plan to use the computer exclusively, i would look into restring the windows boot record.  I have not tried to do this in vista.  In windows xp, you needed to put the cd in and boot into recovery console and type... i think it was 'fixmbr' .  If you typed help you would get a list of valid commands.  Anyway, not sure how different the vista disc is.

---

### Post by racie on 2009-02-08
> **empthollow said:**
> i assume you are using grub as it is default in xubuntu.  edit the /boot/grub/menu.lst file on you xubuntu partition and remove the entry for xubuntu.  if you plan to use the computer exclusively, i would look into restring the windows boot record.  I have not tried to do this in vista.  In windows xp, you needed to put the cd in and boot into recovery console and type... i think it was 'fixmbr' .  If you typed help you would get a list of valid commands.  Anyway, not sure how different the vista disc is.

Erm... I'm not that computer-savvy. Can you explain this to me in a simplified way?

---

### Post by empthollow on 2009-02-08
the menu that you see when you turn on your computer is a bootloader (program that loads operating systems) called grub.  the listing you are seeing is determined by a text file located on your xubuntu partition at /boot/grub/menu.lst.  a bootloader is written to the master boot record which is where the bios looks when it is done.  In the case of grub, the part written on the mbr(master boot record) looks at the file on your xubuntu partion to know what to display on that first screen and how to load it.   

If you want to remove the xubuntu entries in the grub menu, you can edit the /boot/grub/menu.lst file, but keep in mind that your booting vista is still dependant on the menu.lst file on your xubuntu partition.  If you want to reinstall xubuntu, it will also reinstall grub and you will have 2 working boot options at your boot screen.  If you do not plan on using xubuntu and want to wipe that partition and use it for space or something else, you would want to reinstall the windows bootload as it does not look at the partition you want to erase.

hope that's a little clearer and at the same time not waayy more than you wanted to know.

---

### Post by racie on 2009-02-08
Hmm... sort of.  Thanks for your help, but I have some more questions.  First of all, I cannot use Xubuntu, it's corrupted.  So how do I keep the Ubuntu and Vista options on the boot screen?  Do you know where this file is and how to edit it safely?

---

### Post by personjerry on 2009-02-08
you should be able to find it via your ubuntu partition, especially if you installed it after xubuntu, it should be in /boot on one of the partition(s?)

---

### Post by racie on 2009-02-08
I installed both Ubuntu and Xubuntu through Wubi, so it automatically partitioned itself.

---

### Post by empthollow on 2009-02-08
your best bet is to boot the xubuntu (or any ubuntu live cd).  if memory serves you can launch the partition editor (gparted) and it will mount all hard drive partitions.  Then open a terminal and type this.

```
sudo thunar
```
depending on what xubuntu calls the directory you need to navigate to your xubuntu partion (will be in the /media directory) and then into the 'boot' folder and then into the 'grub' folder and open the menu.lst file.

here is a page i reference for addition info on grub
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by racie on 2009-02-09
I do not have any LiveCD's.  I installed both Xubuntu and Ubuntu from Wubi.  I do not wish to use Xubuntu and I uninstalled it, but accidently corrupted it.  Does that make sense?

---

### Post by racie on 2009-02-09
Bump.

Does anyone know how to explain this to me?  =P

---

### Post by rweaver4 on 2009-02-09
If you are running WUBI you are actually running the windows master boot record.
Back up your system or at least set a system restore point first.

In windows go to your control panel and click on 'system', then select the 'advanced' tab. Click on the startup and recovery 'settings' tab where you will find an 'edit' tab under system startup.
Click the edit tab and you will find a list of your startup options where you can delete the line containing the operating system you no longer need. This does not delete any programs, merely the reference in the startup menu.

Hope this helps
Robert

---

### Post by racie on 2009-02-09
Thanks... but I have one more question...

Is there any way to make sure that Xubuntu IS, in fact, completely uninstalled and not just taking up space on my computer?  It is corrupted, so I can't boot it up or anything.

---

### Post by racie on 2009-02-09
Bump.  :?

---

### Post by photon_man62 on 2009-02-09
Yeah. Formatting and purging the Xubuntu partition. Preferably with GPartEd.

---

### Post by photon_man62 on 2009-02-10
Actually, I'll give you instructions. Boot into Ubuntu. Go to System>Administration>Partition Editor. Look for your Xubuntu partition (you can recognize it easily since it will be the only ext3 partition without a mountpoint). Right-click, Format To>(anything, but try ext3 or ntfs for best results). Then right-click, Delete. If Delete is greyed out, then click Unmount. THEN Right-Click>Delete.

There.

---

### Post by photon_man62 on 2009-02-10
Wait a sec, did you just say you installed Xubuntu through Wubi? If so, then boot into Windows, go to the Control Panel>Add/Remove Programs and remove Xubuntu. Then, to make sure, go into the C:\Wubi folder and tell me what you have there.

---

### Post by racie on 2009-02-10
> **photon_man62 said:**
> Wait a sec, did you just say you installed Xubuntu through Wubi? If so, then boot into Windows, go to the Control Panel>Add/Remove Programs and remove Xubuntu. Then, to make sure, search for Wubi. It should find a folder. Go into it and tell me what you can find there.

Yes and this is why I have a problem.  When I went to Add/Remove Programs to uninstall Xubuntu, I forgot to turn off my anti-virus.  Of course, Windows freaked out on me and thought there was a virus.  I had to shut off my anti-virus, but by the time I did, Xubuntu had disappeared from the Add/Remove Programs list.  This has led me to believe that Xubuntu is NOT uninstalled and is just corrupted, however, I am not certain.

---

### Post by photon_man62 on 2009-02-10
Great. Then go to C:\Wubi and tell me what you have in there.

---

### Post by racie on 2009-02-10
Thanks for your help... I'll post back when I boot onto Vista.  (I'm on Ubuntu right now.)

---

### Post by photon_man62 on 2009-02-10
You CAN read Windows (ntfs) partitions with Ubuntu, you know?

---

### Post by racie on 2009-02-10
Hmm... okay... there is no C:\Wubi folder or file, but there is a C:\Ubuntu folder (I'm currently running Vista and Ubuntu as a dual-boot, and previously ran Xubuntu until I uninstalled it..  There isn't a C:\Xubuntu folder either, though.  Oh, there are some files in C:\ called Wubilder and Wubilder.mbr

There seems to be nothing of interest here.  =P

---

### Post by racie on 2009-02-10
Oh, I installed the Ubuntu Partition Manager or whatever it's called through Add/Remove Programs (on Ubuntu), but I couldn't find where it was installed to.  It was not located under Administrator.

---

### Post by photon_man62 on 2009-02-10
What? No C:\Xubuntu? That's quite strange. Then there's a possibility that, despite the antivirus, Xubuntu uninstalled successfully.

And what do you mean you couldn't find it in administrator? You mean /home/administrator?

---

### Post by racie on 2009-02-10
No, I mean I couldn't find it in the start menu thing.  If Xubuntu is uninstalled successfully, then why is it still showing up on the boot screen?  I've uninstalled Ubuntu versions before and they have always been removed from my boot screen options.  Is there any way I can take this off?

---

### Post by photon_man62 on 2009-02-10
Post what the Wubilder file is, then.

---

### Post by racie on 2009-02-10
Most of it consists of random things like this:

> Ãf`&#338;Ãú` À"À¾ &#381;Æf1öf1ÿf¹ $  üfó¥¾ &#381;Æ$þ"À&#381;Ã¹ 1öV¿ |WVüó¥¿&#8222;¾ ¹ ü.fó¥ûËú¸  &#381;Ð¼Üûfaé^ÿ´Í.¬< uöÃ
Missing helper.  X&#381;Ó¼ðÿP&#8364;ú&#8364;r0>þUªu(¾&#8364;¸Kj@ÆèCÿf1À1íöDu
8Tuf&#8249;DEëtÃ   ²é&#8216;ý[Ã&#8364; &#381;Ãè" ¹ 1ö1ÿü.fó§t<&#8230;ít1íf1Àf@uÚ¾¼

I searched the document for anything that says "Xubuntu" and nothing was found.

---

### Post by photon_man62 on 2009-02-10
Did you install Ubuntu (not Xubuntu) through Wubi too?

---

### Post by racie on 2009-02-10
Yes I did.

---

### Post by photon_man62 on 2009-02-10
...

I have no idea how to help you, in that case. Sorry :(

---

### Post by racie on 2009-02-10
> **photon_man62 said:**
> ...

I have no idea how to help you, in that case. Sorry :(

That's okay.  =P  Thanks for trying.

---

### Post by photon_man62 on 2009-02-10
Hold on, I might help you, after all.

---

### Post by photon_man62 on 2009-02-10
You there?

---

### Post by racie on 2009-02-10
Yep. =o

---

### Post by photon_man62 on 2009-02-10
I suspect that you SUCCESSFULLY removed it, but it wasn't able to get to removing it from the bootloader. I can help you fix the bootloader. Are you ready for that, or are you SURE Xubuntu is still on your system?

---

### Post by racie on 2009-02-10
Well, it doesn't show up anywhere on my computer, so I suspect it's gone.

---

### Post by photon_man62 on 2009-02-10
Good. Just in case, search your computer for "xubuntu", then "home" and tell me if anything other than, possibly, something from C:\Ubuntu popped up.

---

### Post by racie on 2009-02-10
Nothing comes up for Xubuntu in a Windows search. =)

---

### Post by photon_man62 on 2009-02-10
K. Now try home.

---

### Post by racie on 2009-02-10
You mean like do a Windows search for 'home'?  About a million things pop up.

---

### Post by photon_man62 on 2009-02-10
Really? Then try .home

---

### Post by racie on 2009-02-10
The same things pop up.  Remember I'm on Vista right now.  What exactly am I searching for?

---

### Post by photon_man62 on 2009-02-10
Anything that might possibly be the home partition of your Xubuntu installation. What about searching "root"?

---

### Post by photon_man62 on 2009-02-10
You there?

---

### Post by racie on 2009-02-10
I searched "root" and nothing seems to be Ubuntu related.  I wish I could stay to chat, but unfortunately I have to leave for a dentist appointment.  *ugh*

Thanks again for all your help.

--Racie

---

### Post by photon_man62 on 2009-02-10
OK. Post when you're done, then.

---

### Post by sharon.gmc on 2009-02-10
How did you know that Xubuntu is corrupted?

---

### Post by photon_man62 on 2009-02-10
(S)he was uninstalling it when her/his antivirus freaked out, thought a virus was removing Xubuntu and stopped it. Xubuntu disappeared from Add/Remove Programs, but it is still in GRUB, but is not bootable.

Got it?

---

### Post by rweaver4 on 2009-02-10
I believe it is in the Windows boot options list (installed via WUBI) rather than grub and the listing can be removed as I detailed earlier. 
Under disk management in the Windows Administrative tools in the control panel you can see the disk usage and where the partions are.

Robert

---

