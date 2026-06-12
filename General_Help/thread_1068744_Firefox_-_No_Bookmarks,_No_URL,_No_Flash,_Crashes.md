---
title: "Firefox - No Bookmarks, No URL, No Flash, Crashes"
date: 2009-02-13
forum: General Help
---

### Post by umechanism on 2009-02-13
Ubuntu 8.10
Fully updated
Firefox 3.0.6
New Dell Studio Desktop

Hello,

I am aware of the issues with Firefox randomly crashing and the ins and outs of using adobe-flash-nonfree, or the flash plugins from Adobe's website.  That is not why I'm posting.  Firefox has learned a new trick:(

When I open FF, this is what I see:
[LIST=1]
[*]A blank start page (used to be Google.com)
[*]No text in the URL field (used to read, "http://www.google.com")
[*]No bookmarks at all (had hundreds of them).
[*]It randomly crashes upon startup.
[*]The "Back" and "Forward" navigation buttons are greyed out and do not function.
[/LIST]

Oddly, FF 3.0.6 works great on this 1996 Compaq that I'm using to post this thread.  No problems at all.

I'm really stumped.  Firefox was working well except for the flash/crashing issues which I was working on.  Now, it is almost unusable.  I've downloaded updates from Ubuntu over the last few days so maybe something got screwed up then.  Not sure.

Does anyone have any idea what is going on?

Thank you.

---

### Post by x33a on 2009-02-13
most likely your profile got corrupted.

you have to create a new profile.

open a terminal and type firefox -ProfileManager, and create a new profile.


as for the bookmarks, you can look under 

/home/username/.mozilla/firefox/profile.default/bookmarkbackups


for the future, use febe addon. it lets you make a backup of all firefox stuff.

[https://addons.mozilla.org/en-US/firefox/addon/2109](https://addons.mozilla.org/en-US/firefox/addon/2109)

---

### Post by umechanism on 2009-02-13
Typing "firefox -ProfileManager" does nothing.  Nothing at all.  Also, there isn't a "Profile" folder in the ~/.mozilla folder.

I think I'll try a full uninstall - again.

---

### Post by umechanism on 2009-02-13
The uninstall/reinstall got the buttons working again but when I tried to import my bookmarks.html file FF crashed.  Every time I tried to import - crash.  Strange. I'll worry about bookmarks later.:(

Now, I'm back to trying to fix the "firefox crashes randomly" and "youtube makes firefox crash" issues.  Any input on these matters would be of great help to me.

Thanks!

---

### Post by x33a on 2009-02-13
firefox crashing randomly could be due to some addon. as for youtube which flash plugin are you using?

---

### Post by umechanism on 2009-02-14
I went to Synaptic and searched for "Flash".  The results included ubuntu-restricted-extras and flashplugin-nonfree.  Are these correct?

---

### Post by x33a on 2009-02-14
yes install flashplugin-nonfree.

---

### Post by umechanism on 2009-02-14
There isn't a "flash-plugin-nonfree" but there is a "flashplugin-nonfree" (no dash between "flash" and "plugin").  I have "flashplugin-nonfree" installed.  Is this the correct one or is there another version that is not in the repository?

---

### Post by Moop on 2009-02-14
That's the right one.

---

### Post by umechanism on 2009-02-14
I thought so.  Well, it is still crashing.  If I visit youtube.com - crash.  Consistently and every time.  I even started FF in safe mode disabling all extensions and plugins but it still crashes.

Is there something else I can try?

---

### Post by Moop on 2009-02-14
Make sure that you don't have more than one version of flash installed like gnash, swf, etc. 

When you completely uninstall Firefox, I don't think it removes the settings in your home folder. You can uninstall Firefox and then go into your home and delete the hidden folder .mozilla (ctrl-h to view hidden folders) and then install Firefox for a clean install.

---

### Post by umechanism on 2009-02-14
I uninstalled FF, deleted the .mozilla folder, reinstalled FF, disabled Shockwave Flash within FF's extensions, and double made sure only one version of Flash is installed.

It still crashes.

Oddly, if I repeat the cycle of launching FF, going to youtube.com, crash (repeat 5 times or so) then finally youtube begins to work.  I just watched several videos without a hitch then suddenly - crash.  Now I'm back to crashing all the time.

I've noticed that it crashes on youtube while FF is loading i2.ytimg.com (as seen on the lower bar of FF).  I wonder it this is causing the crash.

---

### Post by Moop on 2009-02-14
Are you using 64bit or 32bit Ubuntu?

---

### Post by umechanism on 2009-02-14
32 Bit.

Oddly, I'm using 8.10 on two different computers.  The one I'm using to post this message as about 12 years old and has NEVER had a crash when viewing any flash content.  The one giving me all the problems is a new Dell Studio desktop and random crashes are frequent.

---

### Post by x33a on 2009-02-14
it could be one of your addons. list all your addons here.

---

### Post by umechanism on 2009-02-14
Under "Extensions"..

[LIST=1]
[*]Adblock Plus 1.0.1 (crashes with and without this addon)
[*]Ubuntu Firefox Modifications 0.6
[/LIST]

Under "Plugins"

[LIST=1]
[*]Default Plugin
[*]Demo Print Pluging for Unix/linux
[*]Shockwave Flash
[/LIST]

---

### Post by x33a on 2009-02-15
disable ubuntu firefox modifications, and whitelist the website you are trying to view the flash content, with adblock plus.

---

### Post by iamgillespie on 2009-02-17
I had the same problem and mine was fixed very easily.  I simply closed firefox, entered "sudo firefox" into terminal, and restarted firefox and everything came back.  Also I have had trouble getting flash to work. I was originally using Ubuntu 7 and found that I had to update to hardy in order to get the flash plug-in to work. Everything works smoothly for me now. Hope this helps.

---

### Post by umechanism on 2009-02-17
I got all my bookmarks and settings working again but it STILL crashes.  I'll try "sudo firefox" but I shouldn't have to run it as root to make it work.

Why doesn't it crash on my old computer?  Is this a hardware issue?

Frustrating...:(

---

### Post by x33a on 2009-02-17
i think you can try testing your ram with memtest86+.

---

### Post by umechanism on 2009-02-24
> **x33a said:**
> i think you can try testing your ram with memtest86+.

Synaptic indicates that I have memtest86+ already installed but I do not understand how to start the program.  I tried using the terminal but nothing happened.  How do I start/use this program.

Also, isn't all the memory checked during startup?

It has been a week since I first posted - still crashing. ](*,)

---

### Post by x33a on 2009-02-25
when you boot the computer, there is an option for memtest in the grub menu. select and run it from there.

---

### Post by kruschev on 2009-02-25
I had trouble with firefox crashing and fixed it by removing all the swf related stuff. ie. you type "aptitude search swf", go through the list, and "sudo aptitude remove X" where X is the stuff pertaining to firefox.

---

### Post by umechanism on 2009-02-27
> **kruschev said:**
> I had trouble with firefox crashing and fixed it by removing all the swf related stuff. ie. you type "aptitude search swf", go through the list, and "sudo aptitude remove X" where X is the stuff pertaining to firefox.

When I search, I get this:

```
michael@ubuntu-dell:~$ aptitude search swf
p   librfxswf-dev                   - RFXSWF library for SWF (Flash) generation 
p   libswf-perl                     - Ming (SWF) module for Perl                
p   libswfdec-0.6-90                - SWF (Macromedia Flash) decoder library    
p   libswfdec-0.6-90-dbg            - SWF (Macromedia Flash) decoder library    
p   libswfdec-0.6-dev               - SWF (Macromedia Flash) decoder library    
p   libswfdec-0.7-1                 - SWF (Macromedia Flash) decoder library    
p   libswfdec-0.7-1-dbg             - SWF (Macromedia Flash) decoder library    
p   libswfdec-0.7-dev               - SWF (Macromedia Flash) decoder library    
p   libswfdec-0.8-0                 - SWF (Macromedia Flash) decoder library    
p   libswfdec-0.8-0-dbg             - SWF (Macromedia Flash) decoder library    
p   libswfdec-0.8-dev               - SWF (Macromedia Flash) decoder library    
v   libswfdec-dev                   -                                           
p   python-rfxswf                   - Python wrapper for the rfxswf library     
p   python2.4-rfxswf                - Python wrapper for the rfxswf library     
p   pyvnc2swf                       - screen recording tool with Flash (SWF) out
v   swf-player                      -                                           
p   swfdec-gnome                    - Tools to play SWF files (Macromedia Flash)
p   swfdec-mozilla                  - Mozilla plugin for SWF files (Macromedia F
p   swfmill                         - xml2swf and swf2xml processor             
p   swftools                        - Collection of utilities for SWF file manip
michael@ubuntu-dell:~$ 

```

Should I remove all of these?

---

### Post by umechanism on 2009-03-06
> **x33a said:**
> when you boot the computer, there is an option for memtest in the grub menu. select and run it from there.

My computer passed the memtest.  What else can I do?

---

### Post by umechanism on 2009-03-13
Bump.

Firefox, and now Opera, are both crashing more often than the stock market.  I just can't seem to get this resolved.  Could Pulse Audio be causing me problems too?

---

### Post by s3lekta on 2009-03-13
> **umechanism said:**
> When I search, I get this:

```
michael@ubuntu-dell:~$ aptitude search swf
p   librfxswf-dev                   - RFXSWF library for SWF (Flash) generation 
p   libswf-perl                     - Ming (SWF) module for Perl                
p   libswfdec-0.6-90                - SWF (Macromedia Flash) decoder library    
p   libswfdec-0.6-90-dbg            - SWF (Macromedia Flash) decoder library    
p   libswfdec-0.6-dev               - SWF (Macromedia Flash) decoder library    
p   libswfdec-0.7-1                 - SWF (Macromedia Flash) decoder library    
p   libswfdec-0.7-1-dbg             - SWF (Macromedia Flash) decoder library    
p   libswfdec-0.7-dev               - SWF (Macromedia Flash) decoder library    
p   libswfdec-0.8-0                 - SWF (Macromedia Flash) decoder library    
p   libswfdec-0.8-0-dbg             - SWF (Macromedia Flash) decoder library    
p   libswfdec-0.8-dev               - SWF (Macromedia Flash) decoder library    
v   libswfdec-dev                   -                                           
p   python-rfxswf                   - Python wrapper for the rfxswf library     
p   python2.4-rfxswf                - Python wrapper for the rfxswf library     
p   pyvnc2swf                       - screen recording tool with Flash (SWF) out
v   swf-player                      -                                           
p   swfdec-gnome                    - Tools to play SWF files (Macromedia Flash)
p   swfdec-mozilla                  - Mozilla plugin for SWF files (Macromedia F
p   swfmill                         - xml2swf and swf2xml processor             
p   swftools                        - Collection of utilities for SWF file manip
michael@ubuntu-dell:~$ 

```

Should I remove all of these?

bump on this, i got quite a similar problem aswell :-(

---

