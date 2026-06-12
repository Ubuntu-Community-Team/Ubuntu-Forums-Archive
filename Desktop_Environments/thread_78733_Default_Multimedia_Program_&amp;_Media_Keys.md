---
title: "Default Multimedia Program &amp; Media Keys"
date: 2005-10-18
forum: Desktop Environments
---

### Post by whitewizardcoder on 2005-10-18
Hi,

I've recently downloaded amaroK and found that it is a very good alternative to the default Rythembox media player in Ubuntu.  Unfortunately, the media keys (play/pause, stop,...) on my keyboard don't work with it, and it does not get launched when i hit the "launch default music player" program button.  Is there any way to set amaroK as my default player and to get the multimedia keys working?

Thanks,
WhiteWizardCoder

---

### Post by faizulzone on 2005-10-18
i think u should try this

go to System> Preferences> Keyboard Shortcuts.. try to edit multimedia shortcut.. hope its help

---

### Post by Dr. Nick on 2005-10-18
[QUOTE=faizulzone]i think u should try this

go to System> Preferences> Keyboard Shortcuts.. try to edit multimedia shortcut.. hope its help[/QUOTE]

Yes that can edit the shortcuts but unfourtnately cant change what applications launch :( 
to skip back/forth you have to configure it in amaroK, I believe its possible, but about changing default player I dont know, but I want to . 
Their is a similar thread on this aswell concerning beep, that solution was a plugin for beep to set keys [http://ubuntuforums.org/showthread.php?t=77429](http://ubuntuforums.org/showthread.php?t=77429) I will continue to look when I remember to, but hopefully someone will step in and solve this :) hint.. hint..

---

### Post by whitewizardcoder on 2005-10-19
The play/pause media keys needed to be configured in amaroK.  Now they run fine, but I still dont know how to make it the default music player, or, for that matter, to configure xine as the default video player.  Maybe the folks at Ubuntu can help us (hint...hint) :p!

Thanks for the help!

---

### Post by NiceGuy on 2005-10-25
Hi all, I've just been trying to do a similar thing my self with little luck, the best solution I could come up with is 'dirty' to say the least!

I removed Rhythembox so when I pressed the media key on my keyboard it came up with the error message:

"Couldn't execute command: rhythmbox
Verify that this command exists."

I then made a shell script called "rhythmbox" which launched the media player I wanted to use (in my case 'muine') and put it in /usr/bin

hope this helps!

---

### Post by Dr. Nick on 2005-10-25
[QUOTE=NiceGuy]Hi all, I've just been trying to do a similar thing my self with little luck, the best solution I could come up with is 'dirty' to say the least!

I removed Rhythembox so when I pressed the media key on my keyboard it came up with the error message:

"Couldn't execute command: rhythmbox
Verify that this command exists."

I then made a shell script called "rhythmbox" which launched the media player I wanted to use (in my case 'muine') and put it in /usr/bin

hope this helps![/QUOTE]


Clever, I'll have to remember that. Thanks

---

### Post by whitewizardcoder on 2005-10-25
Wow, that's amazing!  I got amaroK running through the script!  Thanks for the hack!

WhiteWizardCoder

---

### Post by NiceGuy on 2005-10-26
My pleasure! By the way if you (or anyone else) comes up with a better way of doing this, please post as this solution is 'functional' if not very elegant. A better way would be to change the default player (or what the 'keyboard shortcuts' program thinks is the default program) - but I'm a bit stumped with that one!

---

### Post by Deusiah on 2005-10-31
I did a lot of searching for this one as it was driving me crazy, eventually I found where it was defined, it's hardcoded into Gnome:
```
case MUSIC_KEY:
    execute ("rhythmbox", FALSE);
    break;
``` This leaves you with four options, edit the Gnome source and recompile, personally I couldn't be bothered with the hastle of this.

Make a Symlink or Shell file that links to or opens Muine and place it in place of /usr/bin/rythembox (as mentioned above).

Use a third party program such as xbindkeys to do the job.

Use Gnomes user defineable shortcuts which is the method I opted for.

---

### Post by ibanez88 on 2005-11-14
I'm having a similar difficulty with my multimedia key.  I want to get streamtuner to come up by default as I don't keep a music library on this computer.

Deusiah, could you possibly elaborate on what you mean by Gnome's user definable shortcuts?

---

### Post by metasquier on 2005-11-19
I am having a very similar problem and its driving me insane.  When I press the volme up and down buttons on my keyboard, it freaking changes the centre channel volume instead of the Front channels.  I assume this is also hard coded? I really think that they should patch this and make these things configurable.

---

### Post by rsay on 2005-11-20
What happens if you right click on a music file, click properties and select the "open with" tab in nautilus? That is how I change the default programs in my setup.

---

### Post by doclivingston on 2005-11-20
[QUOTE=metasquier]I am having a very similar problem and its driving me insane.  When I press the volme up and down buttons on my keyboard, it freaking changes the centre channel volume instead of the Front channels.  I assume this is also hard coded? I really think that they should patch this and make these things configurable.[/QUOTE]

The volume buttons should change the "master" volume, which will affect all the channels. Not doing that would be a bug, what kind of sound card do you have?

---

### Post by Gadren on 2005-11-21
I was able to change it so that my OGG files opened in XMMS (opening them in Totem always made them skip) by right-clicking on an OGG file, going to Properties, and fiddling with the settings on the Open With tab.

---

### Post by ibanez88 on 2005-11-22
Just to be clear, the problem is NOT that I can't open a given file using the program of my choosing.  

The problem is that the "multimedia button" on laptops or stand-alone keyboards seems to be hard-coded to Rhythmbox in Ubuntu.  I don't think it has anything to do with file-type associations, but rather it is a problem with inflexibility in the keyboard mapping options.  Please correct me if I'm not considering the entirety of the issue.

By the way, in response to the request to make Xine the default video player, definitely check the how-to here:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

Worked for me...

---

### Post by clawoo on 2006-02-08
Hi. Umm, try this: [http://www.ubuntuforums.org/showthread.php?p=716602&posted=1#post716602](http://www.ubuntuforums.org/showthread.php?p=716602&posted=1#post716602)

---

### Post by gookie on 2006-02-19
thanks for the tip on the previous posts...I just followed it doing...

Backup rhythmbox on /usr/bin/
```
sudo mv /usr/bin/rhythmbox /usr/bin/rhythmbox_bak
```

Create a new empty file
```
sudo nano /usr/bin/rhythmbox
```

Type in the command for the music player you want to be launched on default. Mine is quodlibet
```
quodlibet
```

Save and exit.

It's all working for me! Thanks! :)

---

### Post by freakzilla on 2006-02-23
Thanks gookie
Worked great for me.

---

### Post by joehill on 2006-02-26
To set metacity's user definable shortcuts, go to Applications -> System Tools -> Configuration Editor.  Then go into Apps -> Metacity -> Keybinding commands and add an application to "command_1" for example. Then set the shortcut by going into "global keybindings" and adding <Ctrl><Shift>a for example under "run_command_1".  I don't know why they don't make these configurations available in the main "keyboard preferences" dialogue--maybe the interface people think it's taking people too far under the hood, but I thought there was something seriously wrong with metacity before I found out that this simple function exists.

---

