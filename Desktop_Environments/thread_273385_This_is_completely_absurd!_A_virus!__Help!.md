---
title: "This is completely absurd! A virus?!  Help!"
date: 2006-10-07
forum: Desktop Environments
---

### Post by Miniberger on 2006-10-07
Something extremely strange has just happened to one of my directories.

I have a Dapper/XP dual boot, and store my data in a shared partition. Within that is another directory with my personal documents. There a bunch of directories within this, and within one is the strangest thing I have seen since I started running Dapper about a month ago. In fact, even windows hasn't done anything like this in a years.

In this directory, there are text files (ones I never created). But not normal text files. MASSIVE text files. Ranging in size from 210 MB to 1.8 GB, about a dozen of them. Yes, I mean it. 9.8 GIGABYTES in all. 

Their names are lines of text from I file I created in a programming envrionment I use in Windows (object oriented turing), whose files are stored in the same parent directory.

Just about the weirdest part is their last modified dates: they range in years from 1902 to 2037. WHAT THE HELL?!

I haven't done anything strange on my system recently. 

To me, a longtime Windows user, this resembles a virus or worm attack. Yet, I am told these things are extremely rare on Linux. Could it be that?

I haven't seen anything like this. Ever.

What I tried to do about it:

I tried deleting them, but it says the directory is read-only. All other directories in the parent say the same thing, but have no giant files. This is a personal folder that I access from both Windows and Linux and I use all the time without issue. I tried to changed owner to me and file permissions to 777, and it did, but it still said read only. 

Summary:

MASSIVE text files (in the GB). Last modified over 100 years ago to 30 years later.

---

### Post by Shay Stephens on 2006-10-07
What do they contain?  Have you done a virus scan on them?  Open with gedit?  Are they still changing file size?

If you determine they can be deleted, can you change the permissions using sudo at the command line or gksudo to open nautilus and change the permissions there?

---

### Post by DavidBell on 2006-10-07
Well if it was windows I would say it sounds like broken _FAT_ (file allocation table) and to try fixing with _chkdsk_ at the risk of losing a significant amount data.

Just new to linux say can't say what the equivalents of the two underlined terms are.

DB

---

### Post by meng on 2006-10-08
I don't know the answer. But to help someone who may know the answer, can you specify what sort of shared partition this is? ext3? fat32?

At a guess, I'd say this is not a virus but something to do with how Windows is writing to the partition. But it's just a guess.

---

### Post by wieman01 on 2006-10-08
Lol... I found this post very funny. Excuse me for that. :-) Funny read!

Could be a virus, yes, but I am sure you got infected & the files corrupted while you were using Windows. It's fairly unlikely that you have caught a Linux worm/virus that does such thing. 

Change the permissions of the file & folders like this:
> sudo chown [COLOR="Red"]your_user[/COLOR] -R *
> sudo chgrp [COLOR="Red"]your_user[/COLOR] -R *
> sudo chmod +w+w -R *

---

### Post by wieman01 on 2006-10-08
Oh yes, I suppose you have got FAT32, right? It's a shared partition so I am assuming...

---

### Post by Miniberger on 2006-10-08
wieman 01, you have every right to laugh at me. Believe it or not, I'm not as new to this as I sounded from that post.

I was kind of in shock when I wrote it because I've never seen anything like it before. But I do realise, of course, it's on a shared partition, so any attack must have come through Windows.

I honestly am laughing at myself right now for not have thinking of that. Sometimes the most plainly obvious things are the hardest to see:D  I see now how stupid that sounds. A linux virus lol...

But yes it is of course a fat32 file format for sharing data. 

I tried that command line you showed (I did a similar thing before, using chown and chmod), but what does the -R option do?

Anyway, it didn't work. These files are trying to make themselves undeleteable. It keeps saying that the file type is read only. Definitely suspicious.

I'm going over to Windows now to check it out with antivirus software.

If anyone has any other suggestions please tell me.

---

### Post by wieman01 on 2006-10-08
> **Miniberger said:**
> wieman 01, you have every right to laugh at me. Believe it or not, I'm not as new to this as I sounded from that post.

I was kind of in shock when I wrote it because I've never seen anything like it before. But I do realise, of course, it's on a shared partition, so any attack must have come through Windows.

I honestly am laughing at myself right now for not have thinking of that. Sometimes the most plainly obvious things are the hardest to see:D  I see now how stupid that sounds. A linux virus lol...

But yes it is of course a fat32 file format for sharing data. 

I tried that command line you showed (I did a similar thing before, using chown and chmod), but what does the -R option do?

Anyway, it didn't work. These files are trying to make themselves undeleteable. It keeps saying that the file type is read only. Definitely suspicious.

I'm going over to Windows now to check it out with antivirus software.

If anyone has any other suggestions please tell me.
I was not laughing at you, don't get me wrong. The whole story simply sounds so odd, it's funny. That's all. :-) Similar strange stuff has happened to me as well...

Let us know if Windows can do anything about it. I am sure you'll work it out. We'll be here if you need assistance.

---

### Post by Miniberger on 2006-10-08
I still find it funny that I considered the prospect of a Linux virus. That's almost as strange as the rest of this.

I know what you mean by so odd it's funny. I've seen trojans, rootkits, and viruses, but never giant mutated text files that make themselves read only (Windows can't delete them either, it gets an error I've never seen before).

It's all so weird. Their filenames, as I noted in the first post, are lines of comments I made in a simple object oriented turing program (I'm just learning the basics). I've never seen malicious files do this before.

The most ominous thing has happened. I tried to do to a local virus scan with norton antivirus 2002 and it generated an error and couldn't scan the giant files. If just gave the message and skipped the entire folder.

This is completely wild. By the way, I'm posting on my other computer (Windows only) because the weird one's internet wasn't loading pages normally (not likely related)

Any ideas on what to do next, anyone? I realise this has left the realm of Ubuntu, but nevertheless... help me please!

---

### Post by DavidBell on 2006-10-08
Soound more and more like broken FAT in need of chkdsk. In Windows XPgo to My Computer, right click the drive, Properties, Tools tab, Check Now, tick both options, OK. Be aware that this can destroy data in other files on the drive depending on how bad it is, so back up what critical data you can first.

DB

---

### Post by Miniberger on 2006-10-08
"Sounds more and more like broken FAT in need of chkdsk."

Oh really? That's interesting, I'll have to try that out. I don't have time now but thanks for the idea.

I was almost certain this was some kind of attack, but maybe not.

Is this type of thing common?

---

### Post by Miniberger on 2006-10-08
Oh and just a note: I can still access most of this partition fine, it's only the one set of directories.

---

### Post by igknighted on 2006-10-08
what if you tried installing clamAV in ubuntu (which should be unaffected) and checking the files with that?  I've never tried using clamAV on a FAT drive, but it might be worth a shot

---

### Post by wieman01 on 2006-10-08
If all this does not help, I would reformat the partition & do backups before you do so.

---

### Post by DavidBell on 2006-10-08
> **Miniberger said:**
> Is this type of thing common?

It can happen, for eg if there is a power outage at the exact moment the FAT is being updated during write operation. When a FAT is broken files can get truncated or joined others or to random junk on the unused areas of the HDD.

If you can't fix right now I would back up ASAP, worst case is the drive could fail completely and need reformatting.

DB

---

### Post by artinla on 2006-10-08
>  If you can't fix right now I would back up ASAP, worst case is the drive could fail completely and need reformatting.

That is very good advice.  I agree with the poster above that your drive may be failing or at the least you may have a corrupt FAT.  Back up what you need and repartition/format the drive.

---

### Post by Miniberger on 2006-10-09
I backed up everything, went to disk properties, tools, clicked check disk and checked both the boxes (in Windows). It checked the disk when I restarted, fixed the problem, and didn't delete anything else.

My last question is, can I prevent this type of thing from happening again?

Thanks everyone for all of your help.

---

