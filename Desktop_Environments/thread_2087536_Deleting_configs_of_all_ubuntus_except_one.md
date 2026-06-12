---
title: "Deleting configs of all *ubuntus except one"
date: 2012-11-23
forum: Desktop Environments
---

### Post by Max the Happy User on 2012-11-23
Hello!

Probably it's enough to read only [SIZE=3]*what's written in italics below*[/SIZE]. It's likely that the rest of information is irrelevant.

I hope I'll make no mistakes, I post here for the first time. Just in case, I apologize.

I have started using Ubuntu with Ubuntu 12.04, with home partition separated. Then I switched to 12.10 (installed from USB, didn't just upgrade 12.04 to 12.10). While I was on 12.10, I installed kde-desktop (using terminal), and logged in it (once if I remember right).
After that, still being at Ubuntu 12.10, I installed xfce-desktop (using terminal).
Then I installed Xubuntu 12.10 (installed from USB - normal, "correct" installation). Then I installed Xubuntu 12.04 (installed from USB). Then I again installed Xubuntu 12.10.
So now I have Xubuntu 12.10 and I want to install Xubuntu 12.04 back (and very likely to stay with it).

My question is following. During all those installations I was using the same /home partiotion, so all that is now saved there. So when I install Xubuntu 12.04,[I] [SIZE=3]will it be possible to delete all the configuration files of those Ubuntu 12.04, Ubuntu 12.10, kde-desktop (and, maybe Xubuntu 12[SIZE=3].[/SIZE]1[SIZE=3]0 [/SIZE]configuration files, which will not be needed for Xubuntu 12.04) from /home partition?[/SIZE]

[/I]In other words, can I make my /home partition look like it never had anything besides Xubuntu 12.04 installed? (And all the applications, of course. I don't want to touch my apps' configs - they must remain)

Thanks in advance!

---

### Post by snowpine on 2012-11-23
Welcome to the forums! :)

I wouldn't worry about it (unless your hard drive is getting so full that a few extra mb's will make a difference). The risk of accidentally deleting something you need outweighs the hypothetical benefits, in my opinion.

---

### Post by Peripheral Visionary on 2012-11-24
I think I would backup all the stuff you want to save onto some external media, then reinstall Xubu 12.04 and format the /home partition, then restore stuff from the backup.  Because the settings you created in 12.10 (which uses Xfce 4.10 I think) won't work as they should in 12.04, which uses Xfce 4.8.  They are different enough to mess things up.

OR, you can choose not to format /home and install Xfce 4.10 in your Xubu 12.04.

---

### Post by Max the Happy User on 2012-11-25
Hello!

Thanks snowpine and Peripheral Visionary!

To  snowpine. I didn't know it was about only a few megabytes - I guess I  really shouldn't worry about them then (though a feeling of having *only necessary files* is nice).
But there is also a factor Peripheral Visionary described - different versions of desktops might be conflicting with each other.

To Peripheral Visionary. Good idea about just backing up, but I don't know exactly which folders & files I should backup. **Where can I find information on /home/ directory hidden files and directories? What are they for? **(because it's all pretty clear with those *Downloads, Music, Documents* etc.)[B]
Also, what if I delete them, will system just create new (hence, default) configs instead of deleted ones?[/B]

And, please, **how to install Xfce 4.10 in Xubuntu 12.04?**


Thanks, people!

---

### Post by Peripheral Visionary on 2012-11-25
> **Max the Happy User said:**
> 
To Peripheral Visionary. Good idea about just backing up, but I don't know exactly which folders & files I should backup. **Where can I find information on /home/ directory hidden files and directories? What are they for? **(because it's all pretty clear with those *Downloads, Music, Documents* etc.)[B] 
Also, what if I delete them, will system just create new (hence, default) configs instead of deleted ones?[/B]


Just back up your music and pics and schoolwork (documents, etc).  When config files are deleted, Xubu uses it's own defaults, which are pretty awesome.  If you just get and install Xfce 4.10 in your Xubu 12.04, you'll probably want to reconfigure stuff anyway.

Click [here]("http://it-diary.com/tutorials/install-xfce-4-10-in-ubuntu-12-04-lts-precise-pangolin/") for instructions on adding Xfce 4,10 (via PPA) to your Xubu Precise, using just a few little commands typed in the terminal!

I haven't done it since I just love my Xfce 4.8 just the way it is thank you, but I've read that the newest version is awesome.

---

### Post by Max the Happy User on 2012-11-25
> **Peripheral Visionary said:**
> Just back up your music and pics  and schoolwork (documents, etc).  When config files are deleted, Xubu  uses it's own defaults, which are pretty awesome.

I dare to correct you: one should also backup all the settings of apps he wants to use. For example, .mozilla (in case you don't want to start again with clear profile in Firefox), .config/cairo-dock (in case you want to get your customized dock bact), etc.
And, of course, one should backup Music, Pictures, Downloads etc. folders.

> **Peripheral Visionary said:**
> If you just get and  install Xfce 4.10 in your Xubu 12.04, you'll probably want to  reconfigure stuff anyway.


Yes, but, as I said, you need your apps' configs.

> **Peripheral Visionary said:**
> Click [here]("http://it-diary.com/tutorials/install-xfce-4-10-in-ubuntu-12-04-lts-precise-pangolin/") for instructions on adding Xfce 4,10 (via PPA) to your Xubu Precise, using just a few little commands typed in the terminal!

Thnx for the link.

> **Peripheral Visionary said:**
> 
I haven't done it since I just love my Xfce 4.8 just the way it is thank  you, but I've read that the newest version is awesome.

I, personally, would stick with the Xfce version present at Xubuntu 12.04. There are a couple o' changes I didn't like in Xfce 4.10.


Anyway, thanks for your help. I guess I'll try to mark the thread as [Solved]. But any future ideas are welcome!

---

### Post by Peripheral Visionary on 2012-11-26
You're welcome and it's okay to correct me any time I goof or forget something important.

I was actually too scared to add the new Xfce to my Xubu Precise, since the "old" Xfce is already so awesome! I didn't want to change anything.  Maybe it's a little paranoia because I've read how the "new and improved" versions of both Gnome and KDE were so terrible, lol.  It might not even be true, but I'm still too new to change alot of stuff yet.

---

