---
title: "[SOLVED] New Ubuntu Lover with some problems... :)"
date: 2008-12-04
forum: General Help
---

### Post by Rohatgir on 2008-12-04
Hi everyone, before I start I would like to thank everyone for the ridiculous amount of information and comments that help new people like me. 

I'm new to Ubuntu, and recently switched over from windows xp as my laptop was running slow and I think that the multi-tasking abilities of Ubuntu increase my efficiency as a college student tenfold. 

I just installed the 8.04 release of Ubuntu about a month ago and love it. I have a dual boot system so I can always revert back. But now my computer is running slow once again, and I don't know whether I have over loaded it. 

1.) Is there a way to optimize my settings and how? (what's going on in the background, or what starts up)

2.) Is there a way to speed up Open Office 3? 

3.) Right now, I have 3 partitions (1 windows, 1 shared (media), and 1 ubuntu). But, every time I log in I have to click on Places --> Storage (name of drive) before Ubuntu recognizes; therefore, I have to re-add all my songs in programs such as amarok. Is there a way to start up with it as an icon on my desktop (I have added it there, but once again, only appears after I click on it once through places)?

4.) What are the differences that would affect me between 8.04 and 8.10? I use my computer for Internet, Office Apps (including pdf editing), and Instant messenger, listening to music - but I do all four at the same time.

Here are my specs for my machine, tell me if this is not possible due to my hardware:

Intel Pentium M proc - 1.60 Ghz
2 gb Ram
120 gb Hard drive
128 Ati Mobility x300 dedicated video memory
I think that's what's mainly important, if there is anything else just ask!

Thanks again for all your help, I know this is long winded, but I couldn't find all the answers in a detailed enough answer for me :)

If there are previous "how-to" guides or forums that I may have missed, just copy paste them :)

---

### Post by gettinoriginal on 2008-12-04
I can't answer your specific problems, as I am new myself.  But just a hint.  Instead of doing your search in the forums, go to google and put the following:

ubuntu forums (your specific need)

This will give you more specific results.

---

### Post by Phases on 2008-12-04
Ok. I'm only a few months into Ubuntu myself so bear that in mind. But I think what you need to do is set that partition up to mount automajically in fstab.

Go here, and scroll down to "Mount the Drive" near the  bottom and read that on down. 

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Hope that helps.

As for trying to optimize. There's all sorts of ways I'm sure. But all *I* can say, for now.. 

Go to System -> Administration -> Services and also System -> Preferences -> Session  and you should be able to de-select stuff THAT YOU KNOW you don't need, that should help with processes. 

Also you can look at System -> Administration -> System Monitor to get an idea of what's using up the most of your resources, but I prefer htop.

In terminal, CLI, type htop. You'll probably have to install it, if so it'll tell you.  I think just "sudo apt-get install htop" will do it for ya.

As for 8.10 vs 8.04 .. check out [http://ubuntunext810.blogspot.com/](http://ubuntunext810.blogspot.com/)  ...on the right is the list of main new feature I think. I don't think it would benefit you tons. Also [http://ubuntuforums.org/showthread.php?t=886980](http://ubuntuforums.org/showthread.php?t=886980)

As as previous poster said, Google is better for searching. I search like so:

site:ubuntuforums.org my search terms

This is my first attempt to help someone, hope *something* in here is useful for ya.

---

### Post by dabl on 2008-12-04
Welcome!  ):P


> **Rohatgir said:**
> 

1.) Is there a way to optimize my settings and how? (what's going on in the background, or what starts up)



No, there is not **a** way, there are about a zillion ways .... far too many to deal with this way. Start 
[[COLOR="SeaGreen"]**here**[/COLOR]](https://help.ubuntu.com/8.10/index.html)

and google yourself all the way to
[[COLOR="SeaGreen"]**here**[/COLOR]](http://rudd-o.com/en/archives/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that)

> 

2.) Is there a way to speed up Open Office 3? 



I don't know about that -- OOO3 is already faster than OOO2 was. Best performance of OOO is without enabling "Desktop Effects", fyi.

> 

3.) Right now, I have 3 partitions (1 windows, 1 shared (media), and 1 ubuntu). But, every time I log in I have to click on Places --> Storage (name of drive) before Ubuntu recognizes; therefore, I have to re-add all my songs in programs such as amarok. Is there a way to start up with it as an icon on my desktop (I have added it there, but once again, only appears after I click on it once through places)?



You need to edit the file /etc/fstab and set the drive to be automatically mounted at boot time.  Search this forum on "fstab" and one of the zillion threads will be the one you need -- [[COLOR="SeaGreen"]**this**[/COLOR]](http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab) one looks pretty complete.

> 

4.) What are the differences that would affect me between 8.04 and 8.10? I use my computer for Internet, Office Apps (including pdf editing), and Instant messenger, listening to music - but I do all four at the same time.



None of those tasks will be affected by the version difference, AFAIK, except "pulseaudio" in 8.10 might or might not do a great job with your music.  To satisfy your curiosity, and also to test it on your hardware, the smart thing to do would be to make an 8.10 Live CD, and boot that and work with it that way.  If all is good to go, then you could install it.  Your hardware is fine -- there is no significant performance difference in 8.10, for most hardware.

---

### Post by MeURi on 2008-12-04
For point 3, you have to insert a proper line into the */etc/fstab* file, like somehow explained [thread=316508]here[/thread]. Also, note that Google is your friend, in these situations (I found that thread by using Google...). Your shared partition anyway is not formatted as ext3, so you have to change a bit from what you read. Again, use Google, or do a ```
man mount
``` from the terminal, and read the documentation.

For point 4, 8.04 is an LTS release, which means long term support. It has slightly older software, but it will be supported for a longer time than 8.10, and is more stable. If you want the latest software, go for 8.10, but be ready to deal with some issues (again, use Google a lot and search well in this forums). Otherwise stick with 8.04, but you are free to do whatever you prefer :-)

For point 2, there are some general tips to speed up Openoffice, be it 2.4 or 3. Again, in Google search for "ubuntu speedup openoffice" without the quotes: the first three results could be what you're looking for, and the first two are link to Ubuntuforums.

Point 1 is a bit tricky, explain better what your situation is (installed apps, system settings, and so on); there should be a simple solution.

---

### Post by Rohatgir on 2008-12-05
Thanks so much for the info, my main problem is that I can't seem to come up with the proper words that summarize my problem. 

I wish there was a tutorial so I can get the language down. Just looking at that fstab, I get confused, as I don't know how to go into root. I'm going to medschool, but all these new words and abilities to change nearly everything gives me so much freedom, but at the same time I don't want to mess anything up beyond repair.

By the "slow down" I experience, its mainly that when I type it takes a bit for the words to catch up, when dragging a window I see a ghost/trail of it, and when scrolling on a image filled website it goes excruciatingly slow. So just simple stuff I think, nothing like compiling, editing images, or video.

---

### Post by Nathan Sweeney on 2008-12-05
> **Rohatgir said:**
> Thanks so much for the info, my main problem is that I can't seem to come up with the proper words that summarize my problem. 

I wish there was a tutorial so I can get the language down. Just looking at that fstab, I get confused, as I don't know how to go into root. I'm going to medschool, but all these new words and abilities to change nearly everything gives me so much freedom, but at the same time I don't want to mess anything up beyond repair.

By the "slow down" I experience, its mainly that when I type it takes a bit for the words to catch up, when dragging a window I see a ghost/trail of it, and when scrolling on a image filled website it goes excruciatingly slow. So just simple stuff I think, nothing like compiling, editing images, or video.

For the slowdown and trails, have you enabled proprietary drivers for your ATI card?  Go to System -> Administration -> Hardware Drivers and see if there are any proprietary drivers that you can enable.  That would probably solve your issue for that.

AFAIK, Ubuntu still does not enable a root user by default (you can't log in as root).  You must perform commands as root by preceding the command with "sudo" so for example
```
sudo nano /etc/fstab
```

Could you post the contents of your /etc/fstab file and tell us what the partition is that you want to mount automatically?  It shouldn't be too bad to add it to fstab to be mounted automatically at boot.

---

### Post by Rohatgir on 2008-12-05
Had I only read the ATI drivers before I reinstalled everything (for me, it seemed easier to start off to do the whole partitioning thing) Using the propriety drivers gives me all the desktop effects as well! Man, thanks a lot! Now all I need to do is upgrade open office 3 and I think I'm set!

thanks again for all your guys' help!

---

### Post by sambita on 2008-12-05
> **Rohatgir said:**
> 

2.) Is there a way to speed up Open Office 3? 


Try this:

[http://www.stchman.com/speedup_oo.html]("http://www.stchman.com/speedup_oo.html")

it worked for me.

> **Rohatgir said:**
> 
3.) Right now, I have 3 partitions (1 windows, 1 shared (media), and 1 ubuntu). But, every time I log in I have to click on Places --> Storage (name of drive) before Ubuntu recognizes; therefore, I have to re-add all my songs in programs such as amarok. Is there a way to start up with it as an icon on my desktop (I have added it there, but once again, only appears after I click on it once through places)?


In case youre not comfortable editing fstab, you can install pysdm (Applications->Add/Remove). ONce installed go to System->Administration(the one that is not preferences, i dont know how it shows in english cause ive got ubuntu in spanish) and select "Storage device manager"
Select the partition you wish to mount automatically and in the "General configuration" tab select assitant, once there go to the "mount" tab and select "mount on startup"

that should do it. 
If you dont understand something let me konw and ill write it more carefully and try to post some images for you to follow.

glad you're loving ubuntu!:D

Edit: Found this tutorial in the forums, ill post it here just in case.

[http://ubuntuforums.org/showthread.php?t=872197]("http://ubuntuforums.org/showthread.php?t=872197")

---

