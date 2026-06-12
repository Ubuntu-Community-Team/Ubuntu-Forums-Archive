---
title: "Evolution, Thunderbird and Exchange"
date: 2011-12-08
forum: Desktop Environments
---

### Post by linux.girl on 2011-12-08
Hello everyone,

I need some help and advise regarding email clients on Ubuntu 11.10 (64 Bit).

The needs are:

1 - Must be able to migrate outlook PSTs to the new client.

2 - Calendar must be able to sync with MS exchange.

Regarding number 1:

I tried to use readpst (for thunderbird) - but to no avail. I get a NULL error and cannot proceed with the conversion to mbox. I took then a different approach - I opened outlook and exported the outlook psts to a csv file because I read that evolution would be able to import and "digest" the csv file. It didn't work either. I get to the part where it is says it will begin to import the file - it shows the progress bar for a few seconds and then it disappears - and nothing happens.

Does anyone have any suggestions for this issue? I would prefer a solution that involves evolution instead of thunderbird because of number 2, the calendar sync issue. 

From what I understand, evolution has a built in calendar while thunderbird doesn't. What I don't know is how I can sync between the evolution calendar and MS exchange calendar. Is it possible to do it? If yes, how?

I would really appreciate any help this great community has to offer.

Thanks!

linux.girl

---

### Post by linux.girl on 2011-12-09
Hi everyone,

So - any ideas about these questions?

BTW - What is the format used in Evolution? Is it also mbox?

Thanks in advance for any ideas!

linux.girl

---

### Post by typhoon_tip on 2011-12-09
Here I am, spent countless hours on it ! :P

First of all, in my opinion, forget Evolution. It is terrible for me, all HTML email do not render properly. If you don't care about that, use it at your own risk.

The best way to import a PST file is to install Thunderbird for Windows (in Windows... where you have your Outlook files), and let Thunderbird import from Outlook all emails, contacts and whatever else you want to import. Then you can take those data files, and put them straight into Thunderbird of Ubuntu (".thunderbird" hidden folder in "home"), it should work straight away.

Calendar is a bit more complicated than that. I still have to try the solution I have found some time ago, but I will do sooner or later. Let me recover the material and I will post. For now, start to install Lightning plugin in Thunderbird, and get familiar with it.

---

### Post by IanW on 2011-12-09
Try [http://gitorious.org/lightning-exchange-provider]("http://gitorious.org/lightning-exchange-provider") to sync Thunderbird/Lightning with Exchange 2007 or later.

---

### Post by linux.girl on 2011-12-09
Thanks so much for the tip! Unfortunately, it is not working for me, I tried this several times, but Thunderbird crashes in the middle of the import process.

I have no idea why :-( 

I am using windows 7 64 bit, outlook 2010 32 bit and Thunderbird 8 32 bit.

Do you know why it keeps crashing?  

Also, I tried to read the help files on Evolution and I found something strange, Ubuntu related! It says Evolution has a built in option to import pst files, but check this out - they also say that "If the option to import Outlook personal folders (.pst files) is not available under File &#9656; Import &#9656; Import single file &#9656; File type, _**your distribution might have not enabled this functionality."**_

And well, I dont have this functionality  and I wonder why would Ubuntu 11.10 disable it???

(while I am writing, 4th attempt to import psts with mozilla failed, another thunderbird crash).

What do I do?

Thanks!!!

linux.girl

---

### Post by typhoon_tip on 2011-12-09
Try importing selective items, not all at once (email, calendar, contacts... separate them).

---

### Post by frncz on 2011-12-09
To download this, I think you get it from:
[https://addons.mozilla.org/en-us/thunderbird/addon/provider-for-microsoft-exchang/versions/?page=1#version-0.17](https://addons.mozilla.org/en-us/thunderbird/addon/provider-for-microsoft-exchang/versions/?page=1#version-0.17)

but I don't know if it works. I can now see calendars (Ctrl+Shift+c) and create a new calendar by selecting the exchange option and entering [https://exchange](https://exchange)....., my name and password, but my appointments don't show up. I'm not far, but a bit more help would be great

---

### Post by linux.girl on 2011-12-09
> **IanW said:**
> Try [http://gitorious.org/lightning-exchange-provider](http://gitorious.org/lightning-exchange-provider) to sync Thunderbird/Lightning with Exchange 2007 or later.

> **typhoon_tip said:**
> Try importing selective items, not all at once (email, calendar, contacts... separate them).

> **frncz said:**
> To download this, I think you get it from:
[https://addons.mozilla.org/en-us/thunderbird/addon/provider-for-microsoft-exchang/versions/?page=1#version-0.17](https://addons.mozilla.org/en-us/thunderbird/addon/provider-for-microsoft-exchang/versions/?page=1#version-0.17)

but I don't know if it works. I can now see calendars (Ctrl+Shift+c) and create a new calendar by selecting the exchange option and entering [https://exchange](https://exchange)....., my name and password, but my appointments don't show up. I'm not far, but a bit more help would be great

@IanW - Thanks, I will check this out. Do you have experience with it? Does it work well for you?

@typhoon_tip - That's what I did all times, selected mail only - and it still crashes. I have some 80 thousand emails in 10 different pst files - perhaps the size is the problem? Or perhaps I should try and download a 64 bit version of Thunderbird (dont even know if there is one).

@frncz - Thanks, I will try it as well. If I get passed the appointments issue I will certainly let you know.

How about this one here: [http://guzaho.wordpress.com/2011/10/18/thunderbird-as-client-for-microsoft-exchange-2010-server-on-ubuntu-11-10/](http://guzaho.wordpress.com/2011/10/18/thunderbird-as-client-for-microsoft-exchange-2010-server-on-ubuntu-11-10/) ? Does anyone know it or tried it before?

@community - does anyone know a way to restore the option of restoring pst filetype to evolution?

I agree with typhoon that perhaps Thunderbird is a better option, but if I can't import the psts, then I might have to continue and try evolution as well? See which one works first?

Thanks again,

linux.girl

---

### Post by linux.girl on 2011-12-11
I finally managed to import the PST files into Thundrbird! It was crashing because of the size of the PSTs. I imported one at a time, and it worked!

Now -  how do I add these files to the linux thunderbird? What is the location where they should be added?

---

### Post by linux.girl on 2011-12-11
OK - I managed to add the mails - it is in a hidden folder in the home directory.

Now back to the calendar issue: 

IanW - I installed the add-on that you suggested, but can't figure out how to use it. It says to add a calendar, but I dont see anywhere a place where I can choose to do so. Do you have some tips for a beginner with this add-on?

---

### Post by BobMarleyy on 2011-12-11
> **linux.girl said:**
>  IanW - I installed the add-on that you suggested, but can't figure out how to use it. It says to add a calendar, but I dont see anywhere a place where I can choose to do so. Do you have some tips for a beginner with this add-on?

Open thunderbird, click on tools -> add-ons. Type exchange and install exchange calendar add-on. This one [http://gitorious.org/lightning-exchange-provider/pages/Home](http://gitorious.org/lightning-exchange-provider/pages/Home)
Close add-ons tab, click on event and tasks - calendar. In the left-side panel you can see your calendars. right-click there and select new calendar, or use file - new - calendar. You can choose to add a exchange calendar.

From the add-on website: "In the location type: https://$ADdomain\$login@auto
where $ADdomain is your active directory domain and $login is your Exchange username (Not necessarily your email address!). Basically what you enter when login into the Exchange/Outlook web access. For example, if your AD user is EXMPL\bobf, and your mail address is [email]bob.foo@example.com[/email], you enter EXMPL\bobf@auto."

Cheers,
Bob

---

### Post by linux.girl on 2011-12-12
> **BobMarleyy said:**
> Open thunderbird, click on tools -> add-ons. Type exchange and install exchange calendar add-on. This one [http://gitorious.org/lightning-exchange-provider/pages/Home](http://gitorious.org/lightning-exchange-provider/pages/Home)
Close add-ons tab, click on event and tasks - calendar. In the left-side panel you can see your calendars. right-click there and select new calendar, or use file - new - calendar. You can choose to add a exchange calendar.

From the add-on website: "In the location type: https://$ADdomain\$login@auto
where $ADdomain is your active directory domain and $login is your Exchange username (Not necessarily your email address!). Basically what you enter when login into the Exchange/Outlook web access. For example, if your AD user is EXMPL\bobf, and your mail address is [EMAIL="bob.foo@example.com"]bob.foo@example.com[/EMAIL], you enter EXMPL\bobf@auto."

Cheers,
Bob

Thanks - the explanation is great!!! The problem is that you tell me I should click on event and tasks - but I dont have that anywhere :-( The add-on was installed correctly, but I still dont see this option of event and tasks. I am using Thunderbird 8.0 on Ubuntu 11.10.

Any ideas?

---

### Post by IanW on 2011-12-12
You _have_ installed the Lightning calendar plugin, yes?

---

### Post by linux.girl on 2011-12-13
Hi IanW, yes, I did install the plugin - and I still dont have this option and I still cant figure this out - any more ideas?

I am using imap with an account connected to MS exchange.

Thanks a lot in advance!

UPDATE! I see it now - I have no idea why it appeared only this second! I will try the other config you suggested and let you know how it works.

@IanW:

I looked at their site and they say:

"
Will it work with Outlook?Outlook does not store its calendar data in an open standard format, so    Calendar and Sunbird currently do not support Outlook directly. However, you may    be able to export your Outlook events as an .ics or .csv file, and import them    into Sunbird or Lightning using the "Calendar Files" or "Outlook Comma Separated"    file type, respectively. Linux users may find    [this page of some use]("http://outport.sourceforge.net/"). (Follow    [bug 167102]("https://bugzilla.mozilla.org/show_bug.cgi?id=167102") for    more details on Outlook integration)"

So it seems it cannot sync with ms exchange?

---

### Post by linux.girl on 2011-12-13
OK, new stage:

It seems it can sync with outlook, I can create a new calendar, but when configuring, it tells me: error->Hostname part of mailbox is not valid.

Any idea what does it mean?

---

### Post by BobMarleyy on 2011-12-13
> **linux.girl said:**
> error->Hostname part of mailbox is not valid.
Any idea what does it mean?
It might have something to do with the internet location you entered for your calendar. Check the add-on website [http://gitorious.org/lightning-exchange-provider/pages/Home](http://gitorious.org/lightning-exchange-provider/pages/Home)
There is something about usage (and documentation), which explains what you should enter. Anyway, try changing the internet location. Perhaps someone else can help you here, because I do not use this add-on (I use google calendar and its thunderbird add-on). Good luck!

---

