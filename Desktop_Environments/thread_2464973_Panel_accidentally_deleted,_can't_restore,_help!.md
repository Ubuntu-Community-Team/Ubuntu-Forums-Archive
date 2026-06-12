---
title: "Panel accidentally deleted, can't restore, help!"
date: 2021-07-17
forum: Desktop Environments
---

### Post by anarkitty on 2021-07-17
My apologies in advance if I'm a bit of a noob here.

I've done the dumb thing many beginners do, and have deleted my main panel. I tried following the instructions in other threads, and they did not restore anything. Somehow I had a blank panel I accidentally created at the top of my screen, but the main one at the bottom--the one everything is saved on--would not come back. Tried the commands that everyone has posted everywhere and all that has seemed to do is create a blank panel. One massive problem: the program shortcuts that I had on there. When the panel was deleted, I had no way to get to my firefox window that had been running and minimised. I created a start menu just to open a new firefox session to get to this forum. I had important tabs open on that original session and now I cannot retrieve them. I cannot retrieve my original panel. Whatever this restore thing did, it didn't even restore it to how it was when I installed lubuntu in the first place! Just blank! I can't even add a widget for my internet connection, there's no option. But I don't want this one, I want to get back the panel that was there before. Pleeeeeease help. I need to recover that panel and the firefox session that was open on it.

Oh, and my open applications no longer show up on this new panel either.

---

### Post by guiverc on 2021-07-17
You haven't mentioned which release, so whilst we could assume it's a *supported* release of Lubuntu using LXQt and thus you're asking about a `lxqt-panel` it's best if we're not making assumptions.

To switch to your *firefox*, why not Alt-TAB to it?

(many of the system *notification *widgets will re-appear if removed, on next login)

---

### Post by anarkitty on 2021-07-17
It says ubuntu 20.10. I can't even copy anything I check in the terminal because I don't know where my windows are minimising to. I didn't know about alt-tab, at least relieved that's saved. But I already tried restarting once and nothing has reappeared. How do I get it back?

---

### Post by guiverc on 2021-07-17
I wonder if you've actually deleted your panel, or just logged into your system using a different session (ie. if you use an *openbox* session no panel exists until you create one).

I'd just logout and ensure you're logging into the **Lubuntu** session which has a panel.  Three sessions are provided on a *modern *Lubuntu install

- Lubuntu ; for the full experience and what we document in our [manual ]("https://manual.lubuntu.me/stable/")
- LXQt ; a less refined, but purer upstream experience (*few if any Lubuntu tweaks*)
- Openbox ; a pure [openbox]("http://openbox.org/wiki/Main_Page") experience ; so no LXQt panels, only things you configure.

As openbox does not have a panel; it maybe you've just logged into this session.  I had a quick play on a *focal* or 20.04 box I have running besides me (*it's doing a QA-test install so I'm only willing to play minimally as I don't want to impact my testing*) and it's not easy to remove the main panel.  If I recall correctly; I've had it crash and disappear; but a simple logout & login would fix that issue; thus this session reply.

(*When I'm finished with my QA test, I may play some more*)

Also please don't forget, [Lubuntu 20.10 is in it's last days of support]("https://lubuntu.me/lubuntu-20-10-end-of-life-and-current-support-statuses/") so upgrade asap.

---

### Post by anarkitty on 2021-07-17
I've logged out and in an few times, definitely not that. I know I deleted it because I thought I was deleting an icon. I somehow ended up with a new blank panel which I am emergency using for the moment, but nothing is working. The original panel had my mimimised windows, wifi status icon, etc. All the normal functioning things that should be there on default. These aren't on this one and I have no idea how to get them back despite swimming through endless thread searches. Everything people suggest to install, it says I already have (like nm-applet and such). I JUST want it to restore to normal and delete the superfluous one. I don't know where any of my [expletive] windows are going when they are minimised now.

---

### Post by guiverc on 2021-07-17
Personally I'd just re-populate your panel. 

The manual page for the panel is [here]("https://manual.lubuntu.me/stable/5/5.1/lxqt-panel.html")  (*note: it's the stable link I've provided, which is for the 21.04 release of Lubuntu, we keep only two; the latest **stable** and **lts** available for public viewing via link*).

If you're comfortable with terminal & exploring, I'd likely look at

 ```
~/.config/lxqt/panel.conf
```

and see if it's present, erased, or has an issue that's easily fixed with an editor.

I'll provide a pastebin of the file for my [20.04.3 QA-test instal]("https://paste.ubuntu.com/p/jQfkbVgV3n/")l as that's been unaltered as a clean install (*it's the install I'm doing Quality Assurance testing for; our next release*), I'd have to boot a *groovy* or 20.10 box to grab one for your release, but there is a chance I've altered it; if you have a thumb-drive with 20.10 on it; you can get a clean copy from it.

For now though, I'm blank on how you can delete a panel, thus I'm sort of unsure of what your actual issue is  (*I'm wondering if you caused it to be unable to run, thus it's not appearing... that there is no config issue it's a not different issue needing fix, but I'm mentally stuck in circles and not sure what to ask*).

If I enter

```
ps -elf |grep lxqt
```

I see the /usr/bin/lxqt-panel  running; is it running for you?  If you hit the Super key does the menu appear?

---

### Post by anarkitty on 2021-07-17
This is what it shows:
:00:01 /usr/bin/lxqt-panel
0 S anarkit+    3743    3610  0  80   0 - 103137 do_pol 23:35 ?       00

Windows key doesn't open the menu, no.

---

### Post by guiverc on 2021-07-17
I just

```
mv ~/.config/lxqt/panel.conf ~/.config/lxqt/panel_conf
```

on the QA-test install box as a test.

On the next login, as that necessary file isn't present, it gets re-created.  It's actually smaller than the original (filesize), but visually it looks pretty normal to me (*even with a `diff` of what it was, and what is now, I can see the reason for the size change but still can't visually spot differences - but that's likely just m*e).

Did you look at the file I mentioned?  Did any issues appear?

Removing it maybe worth trying; though I'd actually `**mv**` or `rename` it (*what I did so I could perform the `diff` later*).  I'd use `mv` to move the file to another location, so you can restore it to where it was if necessary.. I'm using a QA-testing box so I don't care about anything on my box (*it'll get cleanly installed tomorrow again*) - but I still did the `mv` and not `rm` on this box!

(*please try and use {code} tags in advanced for pastes, and include the command; as the format of your process enquiry isn't clear to me*.  *The lack of super key is useful; I didn't see it in your post when I wrote this reply.. but it makes me want to understand your `ps` enquiry*)

---

### Post by anarkitty on 2021-07-18
I don't know what this means. Rename what to what? I don't know anything about where linux keeps its files or anything like that. I just type what I see verbatim into terminal when I find instructions, so if there's a name that needs to be changed I need to be told how to do that. I showed you above what came up; I don't know how to interpret that in terms of whether or not panel is running, so please tell me what it means. Thanks for being patient, but please assume I know absolutely nothing with all of these instructions. (I have used linux for a while but never had anything major happen so I'm sorry for sounding like an absolute beginner but it is what it is.)

Edit: The above code seemed to do literally nothing. Is there something I'm supposed to follow it up with?

---

### Post by anarkitty on 2021-07-18
Upon another reboot it appears that some of the functionality is back on the panel itself, however there is something still very strange with my start menu and my windows themselves--the appearance is different and there is only an "x" to close the windows; not the usual three icons to minimise or resize.

---

### Post by guiverc on 2021-07-18
Sorry.

The {code} is the formatting tools of this site. If you click "Go Advanced" an extra option appears which allows you to highlight a section with your mouse and then click "#" which wraps it in *code *tags.

Once a section is tagged as being code; a different monospace font is used for it, and it's easier to read (it'll appear in the boxes like some of my lines used).

I'm glad you got part of it back.

Sorry I'm rather wordy; and I try and explain - but I'm not great with support, and my level drops from newbie to advanced rather quickly & inconsistently sorry.

If you can take a picture (PrtScr) save it, and upload to a web site and paste a link (this site allows pictures too, but I wouldn't want to advise with how to) I maybe able to see the issue.

My talking about rename/move was my attempted explanation of 

```
mv ~/.config/lxqt/panel.conf ~/.config/lxqt/panel_conf

```

to attempt to reset the panel back to defaults, but I understand you're already past that and have a new issue with your panel.  Well done on getting some panel back though !

Most window formatting configuration is done by `openbox` which is what Lubuntu uses for that function (LXQt doesn't handle windows; has no close/minimize/maximize as it's not a window manager and is agnostic allowing users to use whatever they wish; Lubuntu uses openbox). The manual page for that section can be found [here]("https://manual.lubuntu.me/stable/3/3.2/3.2.11/openbox_settings.html").

---

### Post by anarkitty on 2021-07-20
Thanks for letting me know. I had to do some manual tinkering and found something that allowed me to reset the minimise and maximise icons as well as close. It must have restored some weird defaults. In any case other things still weren't working properly so I just decided to fresh install anyway, so that was hours of frustration for nothing. Thanks for your help though!

---

