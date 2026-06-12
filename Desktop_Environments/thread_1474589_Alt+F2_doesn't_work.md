---
title: "Alt+F2 doesn't work"
date: 2010-05-06
forum: Desktop Environments
---

### Post by anoopsinha on 2010-05-06
Hi

I just installed ubuntu 10.4 (Actually, I installed kubuntu and did a "sudo apt-get install ubuntu-desktop").

My problem is that the Alt+F2 keyboard shortcut doesn't work in GNOME (it works fine in KDE).

I checked the settings in System > Preferences > Keyboard shortcuts. I tried changing this shortcut to other combinations. But, the Run Application dialog box refuses to appear.

Any help would be appreciated.

Thank you.

Anoop

---

### Post by MidnightSon on 2010-05-06
Using GNOME here, the shortcut works fine.
Could it come from the installation kunbuntu>ubuntu ?

---

### Post by HarrisonNapper on 2010-05-06
Hm, maybe check System>Preferences>Keyboards and Layouts in Gnome. Alternately, search around and see where that is in gconfeditor. Can you right-click the panel and run a command from there? Want to see if it's the keyboard shortcut or the command box that isn't working.

---

### Post by anoopsinha on 2010-05-06
Thank you for your prompt reply.

I can right click the panel and get the run dialog from there (I added a button for this to the panel).

Tried gconf-editor. I got lost in the maze ;) I did not find find any relevent entries, though.

---

### Post by anoopsinha on 2010-05-06
Found out what was wrong! I had some old config files (.gnome and others) lying around (my home folder is on a separate partition). I just deleted all the hidden files in my home folder and everything was working as it should!

---

### Post by tomek_wap on 2011-11-01
Same here, doesnt work here on latest ubuntu 11.

tried the solution with CompizConfig (all was set OK in GNOME Compatibility), also checked the Keyboard short-cut, also was OK.

Alt-F2 still doesn't work.

Pls help.

---

### Post by mcduck on 2011-11-01
> **tomek_wap said:**
> Same here, doesnt work here on latest ubuntu 11.

tried the solution with CompizConfig (all was set OK in GNOME Compatibility), also checked the Keyboard short-cut, also was OK.

Alt-F2 still doesn't work.

Pls help.

Do you mean 11.10? There is no such thing as Ubuntu 11, it's either 11.04 or 11.10. (the first number tells the release year, the second one is the release month)

What desktop are you using? Unity or Gnome Shell, or perhaps somehting else?

If you are using Unity, go to CompizConfig, and under Unity-plugin's settings, on the Behaviour-tab, make sure "Key to execute command" is set to "<Alt>F2".

The Gnome compatibility and keyboard settings options are related to old Gnome-panel, which provided the Run dialog in Gnome 2. Ubuntu 11.10 however uses Gnome 3 and the Run dialog is provided by Unity.

---

### Post by tomek_wap on 2011-11-01
my apologies for my ignorance :)

Ubuntu 11.10 it is.
As for the shell: Gnome Classic (Gnome 3 as you say it), if that's what you call it.

And Ive checked it out in Unity, and Alt F2 still doesn't work.
But in some apps and windows when I press Alt, key letters (shortcuts) are being underlined in menu/tool bars.

So maybe there's some conflict with the shortcuts?

---

### Post by mcduck on 2011-11-01
No, the Alt key can definitely be used for both application-specific shortcuts and the run dialog at the same time. But of course you scould check that you haven't got Alt-F2 combination binded for something else.

What comes to Gnome 3, at least with Gnome Shell defining Alt-F2 through keyboard shortcuts should work. It worked for me, the shortcut wasn't enabled by default for some reason so I added it there and it's working now.

I'm not sure about the classic/fallback mode though.

If nothing else works, you could install some third-party program for the purpose and define the shortcut to open that one. I've used both gmrun and alawalk on my Openbox desktop and both seem to do the job fine. Here are some more options: [http://www.omgubuntu.co.uk/2010/11/omg-5-five-ways-to-add-altf2-fun-to-unity/]("http://www.omgubuntu.co.uk/2010/11/omg-5-five-ways-to-add-altf2-fun-to-unity/")

---

### Post by tomek_wap on 2011-11-01
it seems to me that there's a problem with running this specific app/command using shortcuts. ive even assigned different key combinations and nothing.

other shortcuts work, like opening terminal with alt+control+t.

even did a custom shortcut, and nothing...
for now i have an option to run it via applications drop down menu, but i would prefer a quicker way.

will look at that web site you provided with.

---

### Post by tomek_wap on 2011-11-01
all fine now :)

turned off unity as i dont use it , turned on gnome compatibility - just in case one was to go into conflict with the other 

REBOOT - that's all it was needed for alt+f2 to work again :)

Thought Ubuntu was more clever ;)

---

