---
title: "Where are Empathy logs?!"
date: 2009-05-19
forum: General Help
---

### Post by galvao on 2009-05-19
Greetings. 

I've recently switched to Empathy and I'd like to delete some foolish logs, but I can't seem to find where Empathy save them, even reading through the documentation.

Any ideas where they are stored on disc? Is it safe to delete the files, or is there any interface procedure for this?

TIA,

---

### Post by ganesanrajesh on 2009-05-25
Hi,
It's here:D:
~/.gnome2/Empathy/logs
Regards,

---

### Post by galvao on 2009-05-25
Thank you!

---

### Post by smarts53 on 2009-10-18
Ive got the same issue, but I don't see any empathy folder in ~/.gnome2/.
I looked in ~/.config/ as well and found an empahy folder but nothing about logs.

Appreciate any help

---

### Post by Merk42 on 2009-10-29
Bumping this thread because Karmic Koala came out and I can't see the logs in any of the aforementioned places either.
I even looked in **~/.gconf/apps/empathy/conversation** but that folder is blank even though I deliberating chatted to create a log

---

### Post by nyilas on 2009-10-31
Hi,
logs are in **~/.local/share/Empathy/logs**

---

### Post by gypsumwolf on 2009-11-01
Are all conversations auto-logged? And are they ever deleted without user input?

---

### Post by .:Justus:. on 2009-11-12
For those people who didn't find the empathy folder in the Gnome2 directory:

They can also be located here : ~/.local/share/empathy

You must enable "view hidden files" in the view tab in order to see program folders such as ".local" in your home directory.

---

### Post by buzzbo on 2009-12-03
fwiw I use this when I'm looking:

```
find ~ -iname '*empathy*' -print
```

Also, these are xml files.  They don't view well in a text editor.  How best to view them?

---

### Post by ardchoille42 on 2010-03-29
Thanks for the location. Yet something else I have to add to my cleanup.sh script:

```
rm -rf .local/share/Empathy/logs/*
```

I get so tired of developers assuming they can just fill MY hard drive up with anything they want.

---

### Post by darolu on 2010-04-10
> Also, these are xml files. They don't view well in a text editor. How best to view them?
Some 'text-editors' like bluefish 2.0 make it easier to handle long xml files; opening in Firefox should help too; the actual way to do it is to create a CSS for your xml you can use the stylesheet adding this line after your <?xml?>:
```
<?xml-stylesheet type="text/css" href="path/<yourstylesheet>.css"?>
```

Back on topic; thanks for the logs location. Is there a way to configure Empathy so it won't logs all my conversations?

> I get so tired of developers assuming they can just fill MY hard drive up with anything they want.
QFT

---

### Post by zer010 on 2010-06-25
I'd like a cleanup.sh script, and a how-to on implementation. That sound really useful.

---

### Post by AquaFox90 on 2010-08-08
> I get so tired of developers assuming they can just fill MY hard drive up with anything they want.

Agreed. This is something I see in Windows a lot. Software would do stuff for you without your permission. I love Linux because I know what's going on on my computer and I have control and give permission of my software. Empathy should fix this, out of principle.

---

### Post by varanasi on 2010-10-19
This is not among empathy's best features (which I'm still looking for!)  Autologging is enabled and can't be disabled?  And yet, I can't easily read either the chats I want logged or those I don't?  

It looks as if it is [fixed in Meerkat]("https://bugs.launchpad.net/empathy/+bug/411898")?  I wonder whether it will trickle down to those of us who are LTS fans?

---

### Post by sgreimer on 2010-10-20
Update - I finally found my Empathy 2.32 logs at
~/.local/share/TpLogger/logs/TpLogger/logs

---

### Post by GWBouge on 2010-10-22
> **sgreimer said:**
> Update - I finally found my Empathy 2.32 logs at
~/.local/share/TpLogger/logs/TpLogger/logs

Thank You!  I've been looking for where they decided to stuff the logs now for a couple hours, lol.

---

### Post by Funcan on 2010-11-03
For those who want to, you can turn off logging in chat preferences.

---

### Post by GWBouge on 2010-11-05
> **Funcan said:**
> For those who want to, you can turn off logging in chat preferences.

*Now* you can ... my issue (and I assume the issue of some others) is that by the time I noticed the option to turn logging off, Empathy had already started dumping them somewhere else, making my cron task to delete them useless, and putting week old convo's at the top of a 'new' IM, lol.

---

### Post by Tone303 on 2011-05-12
The new line to delete empathy logs is:

rm -rf .local/share/TpLogger/*

they keep changing where they go and having no option to delete or not keep them. They also continue to fail to add a feature to block people. The makers of empathy are bizarre.

---

### Post by pcm_man on 2011-07-09
Folks I am running Ubuntu 10.10 which I think is the BEST release yet of Ubuntu.

Here is where the log and conversation files for Empathy are kept.

~/.local/share/TpLogger/logs

if you use the Nautilus to browse the directories you will see a sub-directory there with a name that is based on the IM service you are using like *yahoo*. Go into that directory and ALL of your conversations for a contact are kept in a directory by the contacts name. The nice thing about this is that you can be selective about which logs you wish to delete.

If you want to delete all the conversations just issue this command:

rm -fr ~/.local/share/TpLogger/logs

By the way for Empathy 2.23.1 there is an option in the Preferences under the "General" setting to disable logging. It is a check box called "Log conversations". That's it. Like they say, if you know how to do it then it's easy!

---

### Post by mariannebrown on 2011-08-23
From the [Empathy FAQ]("http://live.gnome.org/Empathy/FAQ#Where_does_Empathy_save_files_.28accounts.2C_logs.2C_configuration.29.3F") 
New logs (since Empathy 2.31.4) are saved in ~/.local/share/TpLogger/logs

---

### Post by williamn on 2011-10-18
This is just what I need. Thanks

---

### Post by silviutp on 2012-01-23
I had the same issue and found the solution in this topic. Thanks.

For future , maybe is better to search for the logs using the IM userID, because there is no *empathy* word in the logs filename ...

---

