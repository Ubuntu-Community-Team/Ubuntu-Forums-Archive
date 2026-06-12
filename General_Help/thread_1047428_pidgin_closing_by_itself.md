---
title: "pidgin closing by itself"
date: 2009-01-22
forum: General Help
---

### Post by slimx3m on 2009-01-22
alright, it has been a month now i don't think i could take it anymore.  my pidgin has been closing by itself randomly for a month now without any reasons.  my question is... is there a way for me to know what it might be causing this problem?

---

### Post by ibuclaw on 2009-01-22
Open a terminal (Go into **Applications->Accessories->Terminal**) and type in
```
pidgin
```
The application should produce quite a bit of output into the terminal.
Let it run it's due course, and when it closes unexpectedly, post the output that was created from the application here. (ideally, somewhere around the last 50 lines).

Just click and drag to highlight everything and press **Ctrl+Shift+C** to copy it from the terminal.


Also, can you answer a few questions for verification?
[LIST]
[*]What version of Pidgin do you use?
[*]How much memory (RAM) do you have on your computer?
[*]How long does it take on average for pidgin to close itself?
[*]Are you using pidgin actively when it closes itself? (ie: more than 1-3 conversations going on at once).
[/LIST]
Thanks

Regards
Iain

---

### Post by slimx3m on 2009-01-22
> Also, can you answer a few questions for verification?
[LIST]
[*]What version of Pidgin do you use?
[*]How much memory do you have on your computer?
[*]How long does it take on average for pidgin to close itself?
[*]Are you using pidgin actively when it closes itself? (ie: more than 1-3 conversations going on at once).
[/LIST]

[LIST]
[*]v2.5.2
[*]4GB
[*]Average I would say at least every two days
[*]No, I find that it is close whenever I come back from work.
[/LIST]

I opened pidgin on the terminal and I would just wait until crashes and post the log into this post.

thank you for your quick response.

---

### Post by slimx3m on 2009-01-23
here it is what it made fail.

```

(pidgin:3618): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'AR PL UMing HK Light 9.9990234375'

(pidgin:3618): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='ThaiEngineFc', font='AR PL UMing HK Light 9.9990234375', text='&#65083;'

(pidgin:3618): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='AR PL UMing HK Light 9.9990234375', text='&#19968;'

(pidgin:3618): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Kochi Gothic 9.9990234375'

(pidgin:3618): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Kochi Gothic 9.9990234375', text='&#12398;'
Segmentation fault

```

---

### Post by ibuclaw on 2009-01-23
I have discussed this with an affiliate of mine, and here is he what he had to say (after I cleaned up his language a bit):
> 
on cairo?
cairo is very odd for some reason. on a lot of systems you cannot change the font.
i would tell him to delete .purple and to change the font to the default on his cairo dock and if he is using a cairo pidgin plugin to disable it.
my cairo shouts about all kinds of random stuff. it is a nice dock but it is far from bug free


My cover note to that is:
1) Regenerate your font cache
```
sudo fc-cache -f -v
```
2) Check that you are using all the default fonts in pidgin.
Go into **Tools->Preferences** and click the **Conversations** tab, and ensure that the Default formatting is using the 'Sans' font.

3) Disable any plugins that may appear to use cairo, or change the preferences of an identified plugin to use a saner font style when using cairo.
It's in **Tools->Plugins**.

Regards
Iain

---

### Post by slimx3m on 2009-01-23
i know that it is really weird.  but the weirdest part is that i am not really running cairo and i do not have any plugin on pidgin that has cairo or that is related to cairo.  the dock bar that i am using is awn and i am using default font formating on pidgin.

so i really do not know what it could be.  i check with the pidgin community and i found out that the facebook add-on would be causing pidgin to crash...... but this has been happening to me before i installed such of add-on.

i did the command to clear the fons cashe.  i'll run pidgin again from the terminal and le tyo uknow for an output.

---

### Post by slimx3m on 2009-02-12
i am still ahvin gthe same problem with pidgin.  but i will just wait until next release and upgrade to see if the problem is gone.  so if there are not any more thoughts i will close this post in a week.

thanks for helping

---

### Post by slimx3m on 2009-02-16
alright........

i upgraded pidgin to the last version i am not running any plugins and the font type is the system's.  there is nothing really special about my pidign at all (is customization).

here is what the terminal tell me whenever it "crashes"

```
(pidgin:8654): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Kochi Gothic Bold 9.9990234375'

(pidgin:8654): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Kochi Gothic Bold 9.9990234375', text='&#12356;&#12387;&#12392;&#12358;'

(pidgin:8654): Pango-WARNING **: /usr/lib/pango/1.6.0/modules/pango-hangul-fc.so: cannot open shared object file: Too many open files

(pidgin:8654): Pango-WARNING **: Failed to load Pango module '/usr/lib/pango/1.6.0/modules/pango-hangul-fc.so' for id 'HangulScriptEngineFc'

(pidgin:8654): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'UnDotum Bold 9.9990234375'

(pidgin:8654): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='UnDotum Bold 9.9990234375', text='&#51204; &#51060;&#47564; &#44049;&#45768;&#45796;."'

(pidgin:8654): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'DejaVu Serif Bold Italic 9.9990234375'

(pidgin:8654): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='DejaVu Serif Bold Italic 9.9990234375', text='SUP GUYS
```

Oh!!!! by the way now if doesn't close by itself.  now it just crashes open and i am not able to send and or receive any messages.

any thoughts???

---

### Post by khc on 2009-02-17
> **slimx3m said:**
> 
```

(pidgin:8654): Pango-WARNING **: /usr/lib/pango/1.6.0/modules/pango-hangul-fc.so: cannot open shared object file: Too many open files

```


This sounds like a symptom of a pulseaudio bug, does this happen if you disabled pidgin's sound output also? (Preferences->Sounds->method => No Sound)

---

### Post by montaro23 on 2010-06-05
I have the same problem with pidgin after I updated my Ubuntu to 2.6.31-22-generic kernel
I tried the solutions defined here to change the font and to disable the sounds and in vain.
then I Updated to the latest version of pidgin 2.6 and ran pidgin from shell 
```
#pidgin -d
```
and I got these output after its close

```
(18:17:54) msn: oim Date:{4 Jun 2010 08:04:14 -0700},passport{sergant_a@yahoo.com}
(18:17:54) dbus: Invalid UTF-8 string passed to signal, emitting salvaged string!
(18:17:54) pidgin-libnotify: Conversation is NULL, setting up to check in idle(18:17:54) pidgin-libnotify: Notify Message send has NULL Conversation, going idle(18:17:54) g_log: purple_conversation_get_data: assertion `conv != NULL' failed
(18:17:54) dbus: Invalid UTF-8 string passed to signal, emitting salvaged string!
(18:17:54) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(18:17:54) dbus: The signal "blist-node-extended-menu" caused some dbus error. (If you are not a developer, please ignore this message.)
(18:17:54) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(18:17:54) dbus: The signal "conversation-extended-menu" caused some dbus error. (If you are not a developer, please ignore this message.)
(18:17:54) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(18:17:54) dbus: The signal "blist-node-extended-menu" caused some dbus error. (If you are not a developer, please ignore this message.)
(18:17:54) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(18:17:54) dbus: The signal "conversation-extended-menu" caused some dbus error. (If you are not a developer, please ignore this message.)
(18:17:54) prefs: /pidgin/conversations/toolbar/wide changed, scheduling save.
(18:17:54) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(18:17:54) dbus: The signal "conversation-displayed" caused some dbus error. (If you are not a developer, please ignore this message.)
(18:17:54) dbus: Invalid UTF-8 string passed to signal, emitting salvaged string!
(18:17:54) dbus: Invalid UTF-8 string passed to signal, emitting salvaged string!
Segmentation fault
```

Million thanks in advance for help.

---

### Post by arashi007 on 2010-06-20
I use Ubuntu 9.10 and Pidgin 2.6.2

I accidentally knew it when she told me.

One cute girl in my office can shut down my pidgin by sending an empty character by Yahoo Messenger v10.0.0.1102-enUS.

So she use it to annoy me...but I like it since it's her..xixixii.. ;)

---

### Post by Linuxforall on 2010-06-20
Add Pidgin developer's PPA to get latest pidgin. In terminal paste sudo add-apt-repository ppa:pidgin-developers/ppa

sudo apt-get update and then go to update manager and click on update.

---

### Post by derande on 2010-06-21
tonight for the first time i start pidgin and it opens briefly, logs in and shows some contacts, then shut down.
i've reinstalled with updates and still happening. anyone else?

---

### Post by Linuxforall on 2010-06-21
> **derande said:**
> tonight for the first time i start pidgin and it opens briefly, logs in and shows some contacts, then shut down.
i've reinstalled with updates and still happening. anyone else?

Have you installed gstreamer latest ppa btw?

---

### Post by derande on 2010-06-21
> **Linuxforall said:**
> Have you installed gstreamer latest ppa btw?

no. should i? 
and if not why should that affect pidgin?

edit - i do have gstreamer 0.10xx installed but i install it on my own. would that matter?

---

### Post by derande on 2010-06-21
> **derande said:**
> no. should i? 
and if not why should that affect pidgin?

edit - i do have gstreamer 0.10xx installed but i install it on my own. would that matter?


sorry, the package "gstreamer0.10-plugins-bad 0.1o.19-1~lucid1" failed to install or upgrade.

---

### Post by t36 on 2010-07-05
I'm having the same problem. Pidgin starts, tries to log in and then crashes. I tried switching to the developer's version but to no avail.

I added the output from the terminal in the attachment.

---

