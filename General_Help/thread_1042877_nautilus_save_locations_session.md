---
title: "nautilus save locations session?"
date: 2009-01-18
forum: General Help
---

### Post by sindhu_sundar on 2009-01-18
hi!

I'd like to know if there is a way to save open windows and tabs in nautilus as a session which i can save and restore later?

---

### Post by sonicb00m on 2009-03-03
instlal the nautilus plugins from the repo. There's aplugin you can enable in the setings to do this.

---

### Post by sonicb00m on 2009-03-03
Sorry that was gedit i was thinking of!

---

### Post by jaygo on 2009-04-22
I'm with Sindhu, this would be a great time saver and make rebooting less painful (which is actually frequently necessary for me).

---

### Post by kigali on 2010-02-28
I'm lacking this option for nautilus. I use it all the time in kate & gedit. Looking forward to have it in nautilus!!!!!!!!

---

### Post by rekinyz on 2010-09-09
> **sindhu_sundar said:**
> hi!

I'd like to know if there is a way to save open windows and tabs in nautilus as a session which i can save and restore later?


I'm also with Sindhu! 

Is there any plugin for the nautilus or will it be implemented in the next version?  Save Tabs  will be a very practical function for the nautilus! It's now painful for me that I must close all the tabs and then open them again next time to resume my work.

---

### Post by tg3793 on 2010-12-06
Ok I have an idea on how this could be done but just not the talent. First I'll tell you what I'm doing manually and then the obvious idea to automate it.

Currently I created a folder in my home directory called "Nautilus State" and then I dragged it over to the "Places" panel on the left in Nautilus. Then I manually create a symlink to each of the tabs that I have open (on all ten of my desktops) <-- sheesh :-)

Ok so the obvious answer would be to create a script that could 
1) query each nautilus session that was open and the corresponding tabs.
2) create symlinks in that "Nautilus State" directory.

Anybody have any thoughts on this (or the talent?).

---

### Post by Sylchat on 2011-02-04
Hi,

I don't know if I have talent, but I'm looking into this... I am fed up with Nautilus crashing and restoring an old window session!

I'll let you know!

Syl-

---

### Post by tg3793 on 2011-02-04
> **Sylchat said:**
> Hi,

I don't know if I have talent, but I'm looking into this... I am fed up with Nautilus crashing and restoring an old window session! ... I'll let you know!


That would SOOOOOoooo rOCK !!
... Even if you can't get it going I already appreciate the effort :-)

---

### Post by Sylchat on 2011-02-04
no problem :)

So... I didn't find yet how to get the currently open windows.

But I know where the open windows are recorded when saving the gnome session (System>Prefs>Startup Apps>"Remember Currently Running Application").
It's saved in a x.desktop file with 'x' being a random number in this folder: ~/.config/gnome-session/saved-session

If I grep nautilus on these desktop files, I find another file containing the open windows:
$ grep nautilus *.desktop
10cc816b44b7e29988129681266332110600000018900035.desktop:Exec=nautilus --sm-client-id 10cc816b44b7e29988129681266332110600000018900035 --sm-client-state-file ~/.config/session-state/nautilus-1296817026.desktop

Here you see the session-state *.desktop file containing the path of another *.desktop file in ~/.config/session-state/

For example, if I use the remember button with a nautilus window opened on /usr, I have (in XML):
<slot location="file:///usr" active="TRUE"/>

But it seems the desktop file gets deleted when closing gnome session and generates a new file in .config/session-state/. So where are registered these paths for nautilus to generate the session-state file containing previous open windows?
I don't know... I continue the investigation...

---

### Post by Sylchat on 2011-02-09
Hi,

I made 2 scripts to save and restore a nautilus path to a temp file, but that's not the best solution:

$ cat ~/.gnome2/nautilus-scripts/save-path 
```
#!/bin/bash
echo `pwd` >> ~/paths.txt

```

$ cat ~/.gnome2/nautilus-scripts/restore-path 
```
#!/bin/bash
cat ~/paths.txt | while read l; do nautilus -g 600x500 "$l"; done;

```

But then to remove a path you'll need to manually edit the ~/paths.txt file.

---

### Post by Sylchat on 2011-02-09
I was looking at the nautilus history also (in the "Go" menu), but it's not saved to any file.

From [http://ubuntuforums.org/showthread.php?t=695374](http://ubuntuforums.org/showthread.php?t=695374):
> Nautilus saves a history of the last 10 directories you have visited. When you browse the eleventh directory, the oldest one drops off the list. The history is not saved between sessions and is not written to any file. It lives in the Nautilus process memory and is lost when you logout. 

---

### Post by Sylchat on 2011-02-09
I may have found something, but not giving full path:
wnckprop --list | grep "File Browser"

---

### Post by tg3793 on 2011-02-09
Thanks for keeping up with this. I've been really under the weather for a couple of days so just didn't want you to think your work was going unrecognized or unappreciated.
... Hope to be better in a day or two.

thanks.

---

### Post by FBKK on 2011-02-16
There is a nice and easy way to make rebooting a painless process, one in which most of the running applications from your previous session are saved, like nautilus windows or terminal prompts, they are all saved and automatically started upon reboot. 
I know this works because it's enabled on my Desktop, but I'm on my laptop now, and I can't for the life of me figure out how to enable that option again. I think it was a gconf-editor option, but I don't really remember, so if anyone figures this out, please tell us, as I have become really fond of that option.

Thanks

---

### Post by FBKK on 2011-02-16
After a bit of googling I found that option, and I think

"/apps/gnome-session/options" - auto_save_session 
is the option you are looking for and you can find it in gconf-editor (Alt+F2->Type "gconf-editor"->Enter)

That save the entire session for all the programs that are active and respond to gnome session events (at least nautilus and terminal).

Hope that helps !

---

### Post by tg3793 on 2011-02-17
> **FBKK said:**
> After a bit of googling I found that option, and I think

"/apps/gnome-session/options" - auto_save_session 
is the option you are looking for and you can find it in gconf-editor (Alt+F2->Type "gconf-editor"->Enter)

That save the entire session for all the programs that are active and respond to gnome session events (at least nautilus and terminal).

Hope that helps !

You can also get to this by going to "System --> Preferences --> Startup Applications"
... in the dialogue box that comes up you can go to the options tab.

* However, this is exactly the function that Sylchat has been working so diligently on. This "save session" option doesn't seem to be working on all machines all of the time ... It certainly isn't doing so for Sylchat or myself.

After two or three weeks of health issues I'm just trying to get caught back up on a few things and feel bad that I haven't been able to help Sylchat work on this problem which is going to benefit so many.

---

### Post by Sylchat on 2011-02-18
> **tg3793 said:**
> ...
After two or three weeks of health issues I'm just trying to get caught back up on a few things and feel bad that I haven't been able to help Sylchat work on this problem which is going to benefit so many.

No problem, I am myself very busy with my job on daytime and my studies in the evening... I don't have much time to dig further on this issue. Moreover it seems the saving mechanism depends on Gnome Session Management.

There are 3 apps listed in bash completion:
gnome-session             
gnome-session-properties  
gnome-session-save

If I open a new nautilus window and 'killall nautilus', that window is not restored even if I use gnome-session-save (with/without options) or if I click "Remember Running Apps Now" in the Startup Applications gui (which is gnome-session-properties).


You can have a look at gnome-session package in Synaptic and check what files are installed. Among them, the binary gnome-wm, and the documentation, /usr/share/doc/gnome-session/dbus/gnome-session.html
But this is a documentation for programmers, and not the clearest documentation I've seen...

---

### Post by tg3793 on 2011-06-01
> **Sylchat said:**
> It's saved in a x.desktop file with 'x' being a random number in this folder: ~/.config/gnome-session/saved-session

Hmmm. That was pretty cool. Thanks to your info about "```
~/.config/gnome-session/saved-session
```" I was able to go there just now (after nautilus crashed) and open up all of the files in that directory in gedit. From there I was able to find one of them with "Name=File Manager" on the second line.

Now on the third line of that same file I found "```
Exec=nautilus --sm-client-id 10c423b8ecc2d0ffd3128814239886015700000016710028 --sm-client-state-file /home/scribe/.config/session-state/nautilus-1306908175.desktop
```" (**random # every time I know**)

Hmm "Exec=" I thought to myself.
So I copied the rest of that "```
nautilus --sm-client-id 10c423b8ecc2d0ffd3128814239886015700000016710028 --sm-client-state-file /home/scribe/.config/session-state/nautilus-1306908175.desktop
```" and then pasted it in a terminal. VIOLA! My previous nautilus session was restored.

~~~~~~~~~~~~~~~~~~
~ Other Thoughts ~
~~~~~~~~~~~~~~~~~~

:-) ... I know it's been a long time since I've posted on this thread but I've continued to think about it. Still hope someone can come up with an answer for this.

I have a little more knowledge than I did ten months ago when I last commented on this thread. It seems that there would be a way that a cron job could be set to run once every one or two minutes to save the session (I don't know the command for this yet) and then there would always be a fresh save of our session so we didn't loose what we were last doing in Nautilus.

Not an 'elegant' solution I am sure :-)

---

### Post by Brucevdk on 2011-06-18
> **tg3793 said:**
> I have a little more knowledge than I did ten months ago when I last commented on this thread. It seems that there would be a way that a cron job could be set to run once every one or two minutes to save the session (***I don't know the command for this yet***) and then there would always be a fresh save of our session so we didn't loose what we were last doing in Nautilus.

I took a look at this (how to save the current session programmatically) and it turns out that you have to call *SaveSession* on the gnome-session D-Bus service:

```

dbus-send --session --dest="org.gnome.SessionManager" "/org/gnome/SessionManager" org.gnome.SessionManager.SaveSession

```

If you run into the command *gnome-session-save*, ignore it, from what I can tell it doesn't have this functionality.

For those who are curious as to how I found this out:

[LIST=1]
[*]Found the relevant package for System -> Preferences -> Startup Applications using *apt-file search gnome-session-properties*
[*]Pulled in the source code using *apt-get source gnome-session*
[*]Found the relevant function in *capplet/gsm-properties-dialog.c* with the single statement: *g_debug ("Session saving is not implemented yet!");*
[*]Found a Debian patch inside the *debian/patches* directory named *10_session_save.patch*
[*]Applied the patch using *patch -p1 < debian/patches/10_session_save.patch*
[*]Noticed the D-Bus calls in the *on_save_session_clicked* function
[/LIST]

---

### Post by Sylchat on 2011-08-23
> **Brucevdk said:**
> I took a look at this (how to save the current session programmatically) and it turns out that you have to call *SaveSession* on the gnome-session D-Bus service:

```

dbus-send --session --dest="org.gnome.SessionManager" "/org/gnome/SessionManager" org.gnome.SessionManager.SaveSession

```


Thanks! It does what I was looking for.

Each time I call org.gnome.SessionManager.SaveSession it create a new desktop file in ~/.config/session-state/ called nautilus-*random-nb*.desktop

It contains the list of my open nautilus tabs, including those that were closed some time ago. Why? I don't know yet.

On the other side, the ~/.config/gnome-session/saved-session/*sm-client-id*.desktop file is updated with the new nautilus-*random-nb*.desktop name, on 'Exec=' and 'X-GNOME-Autostart-discard-exec=' lines.

The sm-client-id is given by Session-Manager. (not much info on sm-client-id...)

---

### Post by tg3793 on 2012-06-09
It's been just a hair over a year since I last posted here and about a year and a half since I originally started looking for a solution to this problem.

[COLOR="Silver"]Nautilus has been stable enough for me over the last few months (until recently) that I figured I could just get by with saving a few of my most commonly needed directories in CherryTree (my favorite Hierarchical Note Taking Application) where opening them up was just one click away.

I still don't have anything automated but I would like to share a success that I've had on this.

I'm wondering if either Ubuntu, or Nautilus has changed some things in one of the upgrades that I've done over the past year. Because, when I looked at the ~/.config/session-state/ directory I could see over 50 files there with the name "File Manager" dating back more than a year ago. I only saw "File Manager" as the file name at the time because I was using PC Man. But if you open up that directory in Nautilus you will actually see the name of the .desktop files which will save you a step.

I don't know how often these files are saved. I'm guessing they are saved every time I manually click the "Remember Currently Running Applications" button in the "Startup Applications Preferences". [/COLOR]

In any case I took a look at one of them in Gedit and found the following line [COLOR="Sienna"]**Exec='nautilus' '--sm-client-state-file' '%k'**[/COLOR]

So I did a little tweaking of the command and came up with this:
```
nautilus --sm-client-state-file ~/.config/session-state/nautilus-xxxxxxxxxx.desktop &
```

And it worked beautifully!

[COLOR="Silver"]I tried it out on a couple of the "File Manager" files and it worked great. Now, in saying that I tried it out on a couple of the "File Manager" files I mean to say that I opened the one I wanted up in Gedit to get the actual name of the ".desktop" file needed to put in the place of the "nautilus-xxxxxxxxxx.desktop" from the command above.

Please let me know if this method works for anyone else. And who knows, maybe some talented individual (if this works for others) will create a nifty little nautilus extension that will poll the ~/.config/session-state/ directory where we can choose what date we would like to restore directories from :-)[/COLOR]

---

