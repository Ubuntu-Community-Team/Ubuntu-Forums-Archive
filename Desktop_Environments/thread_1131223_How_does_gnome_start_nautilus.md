---
title: "How does gnome start nautilus?"
date: 2009-04-20
forum: Desktop Environments
---

### Post by rplantz on 2009-04-20
I recently upgraded to 9.04RC and now gnome does not automatically start nautilus when I log on. Thus, there are no desktop icons (until I start nautilus manually).

I created another user, and her gnome starts nautilus automatically when I log in to her account. And I upgraded another machine, and it works fine there. So this is probably not a bug in 9.04RC, but I borked something in my account during the upgrade.

Does anyone know where gnome starts up nautilus when you first log on?

---

### Post by coffeecat on 2009-04-20
Curious. Gnome without Nautilus is a bit like chocolate ice-cream without the - um - chocolate. :(

I don't know the answer but I was intrigued. Several gnome versions ago, you could choose 'save current setup' in the logout dialogue (which I guess would remember that Nautilus is running), but that seems to have disappeared. The nearest I can find is System > Preferences > Startup Applications. If you click on the Options tab and tick the 'Automatically remember...' tickbox, that might do the trick. Of course, you probably won't want that ticked all the time, but doing it once *might* make the system remember Nautilus.

---

### Post by rplantz on 2009-04-20
> **coffeecat said:**
> Curious. Gnome without Nautilus is a bit like chocolate ice-cream without the - um - chocolate. :(

I agree.
> 
I don't know the answer but I was intrigued. Several gnome versions ago, you could choose 'save current setup' in the logout dialogue (which I guess would remember that Nautilus is running), but that seems to have disappeared. The nearest I can find is System > Preferences > Startup Applications. If you click on the Options tab and tick the 'Automatically remember...' tickbox, that might do the trick. Of course, you probably won't want that ticked all the time, but doing it once *might* make the system remember Nautilus.

Thank you, it worked. Now, I hope that somebody can fill us in on the details:

* Where does this info get saved?

* Is there a more direct way to do this?

* And, as you implied, why is Gnome running without Nautilus in the first place?

---

### Post by coffeecat on 2009-04-21
A question: when you say it worked, does that mean you only needed the 'Automatically remember' tickbox ticked for one logout and login, or did you have to keep it ticked permanently? Because if the latter, it's really only half a solution. A bit like vanilla ice-cream with some chocolate sauce poured over it. :p

One other suggestion. It was too late last night when I posted to do more than a cursory look in gconf-editor. That may not be the answer but I'm intrigued enough to have a look later when I boot up Ubuntu (I'm using MacOS atm).

**Edit:** I obviously haven't woken up properly yet. I've got VirtualBox with Jaunty installed. Here's what I've found in gconf-editor:

desktop -> gnome -> session > required > filemanager = "nautilus".

And this what I did:

Create new user (in case everything went pear-shaped)
Login as new user.
Open gconf-editor and removed 'nautilus' from the value field under filemanager. Also went to apps > nautilus > desktop to switch the various desktop icons.
Logged out and in again - no desktop icons.
Ran 'nautilus' from Alt-F2 and a nautilus window opened and the desktop icons appeared.

I wonder if that entry in gconf got corrupted somehow when you did the upgrade. I doubt it was anything you borked. Or maybe it is a bug. Many people don't activate desktop icons so perhaps this doesn't get noticed.

---

### Post by rplantz on 2009-04-21
> **coffeecat said:**
> A question: when you say it worked, does that mean you only needed the 'Automatically remember' tickbox ticked for one logout and login, or did you have to keep it ticked permanently? Because if the latter, it's really only half a solution. A bit like vanilla ice-cream with some chocolate sauce poured over it. :p

I only had to leave the 'Automatically remember' box ticked for one cycle, and nautilus gets started from now on. Somehow, the chocolate sauce got mixed into the vanilla ice cream, turning it into chocolate ice cream. :-)

> 
One other suggestion. It was too late last night when I posted to do more than a cursory look in gconf-editor. That may not be the answer but I'm intrigued enough to have a look later when I boot up Ubuntu (I'm using MacOS atm).

**Edit:** I obviously haven't woken up properly yet. I've got VirtualBox with Jaunty installed. Here's what I've found in gconf-editor:

desktop -> gnome -> session > required > filemanager = "nautilus".

And this what I did:

Create new user (in case everything went pear-shaped)
Login as new user.
Open gconf-editor and removed 'nautilus' from the value field under filemanager. Also went to apps > nautilus > desktop to switch the various desktop icons.
Logged out and in again - no desktop icons.
Ran 'nautilus' from Alt-F2 and a nautilus window opened and the desktop icons appeared.

I wonder if that entry in gconf got corrupted somehow when you did the upgrade. I doubt it was anything you borked. Or maybe it is a bug. Many people don't activate desktop icons so perhaps this doesn't get noticed.

I tried removing 'nautilus' as you suggest. Log out, then back in and the icons are still there.

Another part of the puzzle probably has to do with the files in ~/.compiz/session/. I do not know who produces these files, but when I look at the latest one I see:
```

bob@bob-desktop:~/.compiz/session$ cat 1068ce09a2db3d7ce12402834807151400000111330036 
<?xml version="1.0" encoding="UTF-8"?>
<compiz_session id="1068ce09a2db3d7ce12402834807151400000111330036">
  <window id="10df234ff9036e05e1240263436633900000084550043" title="x-nautilus-desktop" class="Nautilus" name="desktop_window" command="nautilus">
    <geometry x="0" y="0" width="1280" height="1024"/>
    <sticky/>
  </window>
  <window id="1072726da368939410124032816679038200000035350033" title="Inbox (3 unread, 186 total) - Evolution" class="Evolution" name="evolution" command="evolution">
    <geometry x="0" y="25" width="1169" height="874"/>
    <minimized/>
    <workspace index="0"/>
  </window>
</compiz_session>

```
When I was not getting icons I saw one like:
```

bob@bob-desktop:~/.compiz/session$ cat 108e9cd46de08c5c69124025652177884300000035350030 
<?xml version="1.0" encoding="UTF-8"?>
<compiz_session id="108e9cd46de08c5c69124025652177884300000035350030">
</compiz_session>

```
So I have a feeling that compiz is involved in this puzzle. But I don't know where these strange 'session' files come from. As an aside, I wonder if I can delete the old ones.

It's also strange that this Desktop icon problem occurred when I upgraded my desktop machine, but not my laptop.

---

### Post by coffeecat on 2009-04-21
> **rplantz said:**
> I tried removing 'nautilus' as you suggest. Log out, then back in and the icons are still there.

Well, that's very odd. I've tried that twice over now, once in the virtual Jaunty, and once in a native install on my main machine. Each time I created a second user - fred - and each time the desktop icons disappeared when I removed the string 'nautilus' from the filemanager line and relogged in again.

That's what I like about Linux - its complete and utter unpredictablity at times.

I think we've got ourselves a whipped cream, chocolate, raspberry and hazelnut trifle sundae mousse here. :lol:

---

### Post by rplantz on 2009-04-21
> **coffeecat said:**
> 
That's what I like about Linux - its complete and utter unpredictablity at times.

But it's much more predictable than Windows. A few months ago I bought my first Windows machine, so I'm a Windows newbie. I have never seen anything quite as awful as Windows. I can be chatting on Skype, and the machine will simply reboot itself to finish up some sort of "update" it did without even asking!

And I'm not a novice at this. My career with computers started when I took a class in designing flip-flops as an electrical engineering undergrad at Berkeley in 1961. So I've had many years of experience with lots of different systems. I became almost exclusively a Mac user in the middle 80s, adding Linux in the late 90s. 
> 
I think we've got ourselves a whipped cream, chocolate, raspberry and hazelnut trifle sundae mousse here. :lol:
Yummy. :lol:

---

### Post by coffeecat on 2009-04-21
> **rplantz said:**
> A few months ago I bought my first Windows machine, so I'm a Windows newbie. I have never seen anything quite as awful as Windows. I can be chatting on Skype, and the machine will simply reboot itself to finish up some sort of "update" it did without even asking!

Ah yes. The old I-want-to-reboot-so-I-won't-wait-for-your-OK-but-just-go-ahead-even-if-you-haven't-saved-that-important-document-yet Windows trick. 

Since I haven't a clue about whether compiz is involved in the Nautilus business, and since I've had the misfortune to use various incarnations of Windows since MS-DOS 3 (so to speak), let me go completely off-topic and share a couple of Windows stories with you. :)

I won't expose you to the full horrors of the 80s and 90s, but instead I take you to just four years ago. I was the proud owner of a nice new shiny Sony laptop which came with a DVD-writer - the only DVD-writer I had in those days. I was using Windows XP because I had not yet discovered Linux - until someone told me about it. And then I bought a computer magazine which, coincidentally, had the iso for the live DVD of Suse on the cover disc, together with instructions on how to burn it. I was intrigued enough to want to try. I had never heard of ISO9660 before, let alone burned an iso image so, three unusable DVD-coasters each with one large iso file later ( :oops: ) I eventually managed to create a bootable disc. I was impressed. Really impressed. So much so that, now I knew how to burn an iso ](*,), I decided to download an installer DVD, and of course I had to use the laptop. DVD writer, you see.

A 4GB download was going to take about three hours so I made sure the power cord was plugged in. Of course. And I checked on proceedings every quarter of an hour or so. Of course. Everything was fine for a couple of hours, but then I got distracted for about three quarters of an hour and, on returning to the laptop found that it had put itself into standby mode. While it was still downloading an iso. Only 100MB short of the whole file. Would you believe that the default power option setting WITH THE POWER CORD IN is to go into standby after 25 minutes inactivity? Grr. Downloading a file is not activity I suppose. Grrr. Wasted most of that month's download limit. Grrrr.
 

 One good thing came out of it – after that fiasco I was determined to get on with Linux, and get on I did.
 

 Second story: fast forward four years to just a few days ago. That laptop has given good service, but the Windows registry was getting bloated. In case you didn't know, that's a 'feature' of Windows. As time passes it gets slower and slower. So I decided to restore Windows back to the factory condition with the restore discs. Restoring was fairly painless and unremarkable, but then I got to the first boot, create account, configure initial settings stage. A screen came up telling me that it could find no network connection and telling me how to configure networking once the desktop had loaded. Fair enough – I had not connected an ethernet cable - so I clicked on 'next' to be greeted with:
 

 “Do you wish to register online with Microsoft now? Yes/No”
 

 Hmmm. :-k
 

 :lol:

---

### Post by rplantz on 2009-04-21
I left Vista on my laptop and made it dual-bootable with Ubuntu. About the only thing I run under Vista is Skype. For some reason, the sound is low on the Linux version.

Meanwhile, my partner uses Windows at work so is much more experienced with it than I. He set up various malware protections programs on it for me. It seems that I spend more time updating the various malware protection programs than actually *using* Vista.

---

