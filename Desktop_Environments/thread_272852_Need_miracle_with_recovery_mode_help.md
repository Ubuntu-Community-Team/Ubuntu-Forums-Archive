---
title: "Need miracle with recovery mode help"
date: 2006-10-07
forum: Desktop Environments
---

### Post by IusedTObeSOMEONEelse on 2006-10-07
Ias playing around with a puppy linux live cd and some how something with swap and what ever got all mixed up and now my edgy will not boot up. It gets hung up right at the begining and I can get to grub- recovery mode but I do not know what to do. Please I need help!! I swear I'll never play around like that again. I await a knight in shining armor. Sally  ](*,)

---

### Post by aysiu on 2006-10-07
When you say it "will not boot up," can you give some more details?

At what point does it stop? Does it give you any failure messages?

---

### Post by IusedTObeSOMEONEelse on 2006-10-07
Hi Aysiu!  it gets as far as ok booting kernal and then curser goes to the top and thats where it stays.   I have the recovery mode screen in front of me now

---

### Post by aysiu on 2006-10-07
Hm. I'm not sure what to do about that. Could you provide more details about what happened with swap and what sort of playing around you did with the Puppy Linux live CD?

I'm not sure I can help with fixing Edgy, to be honest, but details may be able to help someone else help you.

I could probably help you back up and reinstall... that's about it.

---

### Post by IusedTObeSOMEONEelse on 2006-10-07
well I was playing with memory and disc usage in puppy and I think I changed some thing to swap. I also can not get to puppy with cd as it fails to load. I have a dapper cd from ship it. Is there a way to recover or ahave I got to re-load and lose all data I had on edgy

---

### Post by aysiu on 2006-10-07
You can recover data from Edgy and then reinstall.

A reinstall is a bit extreme. If possible, I would wait a day--see if an expert (which I am not) can hop in and help you with this.

If not, I can definitely help you with saving your files and reinstalling.

---

### Post by IusedTObeSOMEONEelse on 2006-10-07
Thanks for your input. Is there not some thing to type in recovery mode. How do I go about recovering files and all my music. I guess that re-installing wouldn't be so horrible it's just so time consuming (at least 2 to 3 days of downloading , updating , upgrading and updating and so on ) yuk!!

---

### Post by aysiu on 2006-10-07
Well, there very well may be something you type in recovery mode--I just don't know what it is, which is why I recommended waiting a day to see if someone more knowledgeable than I can jump in and help. Weigh one day waiting for help v. two days reinstalling...

The up side is that you can save not only your files but also your settings, so you may have to upgrade and update, etc., but you won't have to reconfigure all your personal settings.

A couple of things that may help you:

1. **[Creating a separate home partition](http://www.psychocats.net/ubuntu/separatehome)**--helpful for reinstalls, as you won't even have to back up your files and settings; they're completely separate from the rest of your Ubuntu

This is one way to recover your files. If you're not interested in that, we can work on another way.

2. For the future, you may want to look into **[making an image of your partition](http://www.psychocats.net/ubuntu/partimage)**--something you may want to do from time to time once you have everything set up perfectly, so that you have an easy way to restore everything without taking two to three days to reinstall.

---

### Post by IusedTObeSOMEONEelse on 2006-10-07
I shall wait it out and see if some one can htlp ouy. I really appriciate your help. I quit cigarettes 3 weeks ago but right now I need to go out and det one.  I don't care if it's 4:30 in the morning. Let's wait and see what happens later on today. tThanks so much: (

---

### Post by anaconda on 2006-10-07
It sounds to me like you are NOT in recovery mode, but you are in grub-command line instead.. (cant be sure though.. what happens if you type: 
ls -la /boot/grub  
if you are in real recovery mode you should see what is in /boot/grub , and if not .. )

grub propably didn't find your kernel or not even your ubuntu partition.. Have you changed anything in your /boot/grub/menu.lst -file recently?

If you boot with liveCD (Ubuntu, knoppix, DSL or puppy) can you see and access your ubuntu partition? (Booting with liveCD and coying files to some safe place is the easiest way to rescue data from nonworking os..)

---

### Post by rogier.de.groot on 2006-10-07
Kernel starting up & cursor staying on top sounds like an X server problem to me... could you try Alt-F1 (or Ctrl-Alt-F1, or Alt-1 or whatever the combo was) and switch to a text-mode terminal? Do you see any services starting?

---

### Post by IusedTObeSOMEONEelse on 2006-10-07
Sorry to late I already re-installed dapper and now i've got to decide how I shall procceed to upgrade to Edgy--make a disc --edit source list -- or go through all the dapper updates and then the upgrade. which would be the quickest? But thanks for your reply. Sally :-?

---

