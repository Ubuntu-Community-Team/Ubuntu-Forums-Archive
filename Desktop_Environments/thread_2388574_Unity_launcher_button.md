---
title: "Unity launcher button"
date: 2018-04-04
forum: Desktop Environments
---

### Post by Skaperen on 2018-04-04
i am running Unity on my Ubuntu 16.04 LTS based laptop (last upgraded yesterday).  i would like to set up a button on the launcher bar that will execute a command line or script of my own.  how do i get started to do that?  some google searches came up empty, but maybe i guessed the wrong terms.

---

### Post by Frogs Hair on 2018-04-04
Have you written the script in gedit, named, saved, and made it executable? If so the next step is to test the script. Creating a desktop entry could allow you to add a launcher and other forum members may be able to help with that. I've not created a launcher for a script in Unity.

---

### Post by monkeybrain20122 on 2018-04-04
Make a .desktop file where Exec=path/to/your/script, make it executable and put it in ~/.local/share/applications. To get a template of a .desktop file, just bring up any .desktop file in /usr/share/applications with an editor.

---

### Post by kerry_s on 2018-04-04
i usually manually do mine:
example:
gedit ~/.local/share/applications/my-app.desktop

inside:
[Desktop Entry]
Version=
Type=Application
Name=
GenericName=
Comment=
Icon=
TryExec=/needs/to/be/full/path
Exec=/needs/to/be/full/path
Categories=

this is my actual 1 i'm using:
[Desktop Entry]
Version=4.0.17
Type=Application
Name=Stremio
GenericName=Media Center
Comment=Watch instantly all the video content you enjoy in one place
Icon=video
TryExec=/home/user/Streamio/Stremio+4.0.17.appimage
Exec=/home/user/Streamio/Stremio+4.0.17.appimage
Categories=AudioVideo;Video;Player;

---

### Post by Skaperen on 2018-04-05
> **Frogs Hair said:**
> Have you written the script in gedit, named, saved, and made it executable? If so the next step is to test the script. Creating a desktop entry could allow you to add a launcher and other forum members may be able to help with that. I've not created a launcher for a script in Unity.

yes, but i used emacs instead of gedit to create it.   it will create more in the future once i know this can be done and how.

---

### Post by monkeybrain20122 on 2018-04-05
> **Skaperen said:**
> yes, but i used emacs instead of gedit to create it.   it will create more in the future once i know this can be done and how.

It doesn't matter which editor you use, the script is just an executable text file.

---

### Post by Skaperen on 2018-04-05
> **monkeybrain20122 said:**
> Make a .desktop file where Exec=path/to/your/script, make it executable and put it in ~/.local/share/applications. To get a template of a .desktop file, just bring up any .desktop file in /usr/share/applications with an editor.

so, the mere existence of a properly constructed and executable .desktop file in that directory causes the button to exist?

---

### Post by Frogs Hair on 2018-04-05
The editor shouldn't matter as long the script is executable and works. See the posts above for help with the desktop entries needed to create the launcher.

---

### Post by monkeybrain20122 on 2018-04-05
> **Skaperen said:**
> so, the mere existence of a properly constructed and executable .desktop file in that directory causes the button to exist?

You have an executable script, the .desktop file (made executable) runs it when click, if you put it in .local/share/applications then it will show up in the dash (may have to logout and log back in), then you can pin it to the launcher.

---

### Post by Skaperen on 2018-04-05
now, how to get the button to appear.  or, perhaps, how to get Unity to reload its .desktop files.  file managers can be notified when things show up in the directory it has open.  so, why can't Unity do this with [FONT=courier new]~/.local/share/applications[/FONT]?

---

### Post by monkeybrain20122 on 2018-04-05
> **Skaperen said:**
> now, how to get the button to appear.  or, perhaps, how to get Unity to reload its .desktop files.  file managers can be notified when things show up in the directory it has open.  so, why can't Unity do this with [FONT=courier new]~/.local/share/applications[/FONT]?

I am not sure what you are asking, I suppose by "the button" you mean the launcher icon?  See Kerry_s's post for the template to make a .desktop file, and the Icon= line has to be supplied by you (point it to a jpg or png file that represents your script) then make the .desktop file executable, put it in ~/.local/share/applications and it will appear in the dash if you search for it (may need a logout/login) and once you find it then you can pin it to the unity launcher like you do with other applications. No, they don't get pinned there automatically and it makes sense, you don't want every single application you install to show up at the launcher, just the "quick launch" ones.

---

### Post by Skaperen on 2018-04-05
log out and log back in is a problem.  too many other things running.  let me see if i can do this as a different user for testing.

---

### Post by monkeybrain20122 on 2018-04-05
> **Skaperen said:**
> log out and log back in is a problem.  too many other things running.  let me see if i can do this as a different user for testing.

Then try run 

```
sudo updatedb
```

No it wouldn't work for a different user since the script and the .desktop files are both in your user's home

---

### Post by kerry_s on 2018-04-05
i think unity has the same restart switch as gnome?

press alt+f2, type r & hit enter

---

### Post by monkeybrain20122 on 2018-04-05
> **kerry_s said:**
> i think unity has the same restart switch as gnome?

press alt+f2, type r & hit enter

No, it is setsid unity, but for some systems that would log you out.  In any case it is not that unity has not refreshed.

---

### Post by monkeybrain20122 on 2018-04-05
BTW, you can check if your .desktop file is working by clicking it, if it works then you can just drag it from .local/share/applications to the launcher bar, that way you don't need to logout or login.

---

### Post by Skaperen on 2018-04-05
under a different user, the button is not showing up after logging out and back in.  i cannot figure out how to get this forum to display text unformatted.  so here is what i think should get the button show up under user *magnatune* (the user i log in to to download music from magnatune.com).

```
lt1/magnatune /home2/magnatune 60> ls -dl .local .local/share .local/share/applications .local/share/applications/playrumi.desktop
drwxr-xr-x  3 magnatune magnatune 4096 May  9  2016 .local
drwxr-xr-x 12 magnatune magnatune 4096 Mar 10 00:55 .local/share
drwxr-xr-x  2 magnatune magnatune 4096 Apr  5 22:55 .local/share/applications
-rwxr--r--  1 magnatune magnatune  224 Apr  5 22:47 .local/share/applications/playrumi.desktop
lt1/magnatune /home2/magnatune 61> cat -n .local/share/applications/playrumi.desktop
     1    [Desktop Entry]
     2    Version=1.0
     3    Type=Application
     4    Name=Rumi
     5    GenericName=Rumi
     6    Comment=play rumi in the background
     7    Icon=music
     8    TryExec=/home2/magnatune/desktop/playrumi
     9    Exec=/home2/magnatune/desktop/playrumi
    10    Categories=Audio;Music;
lt1/magnatune /home2/magnatune 62>
```

---

### Post by again? on 2018-04-05
@ Skaperen,
You may not be aware of this but your .desktop file does not need to be executable to work with the unity launcher.
If the file is correct you can drag and drop to the Unity launcher (sidebar).
However, if you want to test it by clicking on the actual .desktop in the file browser it needs to be executable.
If the .desktop file doesn't work , test your "Exec=" line in terminal, eg **/home2/magnatune/desktop/playrumi**

I usually make .desktop files in ~/.local/share/applications executable because they show differently in the file browser.
When executable the icon and name from the .desktop file is used.
eg Attached Pic shows the same .desktop file executable and non executable.

---

### Post by monkeybrain20122 on 2018-04-06
> **Skaperen said:**
> under a different user, the button is not showing up after logging out and back in.  i cannot figure out how to get this forum to display text unformatted.  so here is what i think should get the button show up under user *magnatune* (the user i log in to to download music from magnatune.com).

[SIZE=1][FONT=courier new]lt1/magnatune /home2/magnatune 60> ls -dl .local .local/share .local/share/applications .local/share/applications/playrumi.desktop
drwxr-xr-x  3 magnatune magnatune 4096 May  9  2016 .local
drwxr-xr-x 12 magnatune magnatune 4096 Mar 10 00:55 .local/share
drwxr-xr-x  2 magnatune magnatune 4096 Apr  5 22:55 .local/share/applications
-rwxr--r--  1 magnatune magnatune  224 Apr  5 22:47 .local/share/applications/playrumi.desktop
lt1/magnatune /home2/magnatune 61> cat -n .local/share/applications/playrumi.desktop
     1    [Desktop Entry]
     2    Version=1.0
     3    Type=Application
     4    Name=Rumi
     5    GenericName=Rumi
     6    Comment=play rumi in the background
     7    Icon=music
     8    TryExec=/home2/magnatune/desktop/playrumi
     9    Exec=/home2/magnatune/desktop/playrumi
    10    Categories=Audio;Music;
lt1/magnatune /home2/magnatune 62>[/FONT][/SIZE]
??? !!!

I am not sure what you are doing, seems that you make the task very complicated for no reasons. Here is an example

I compiled gimp 2.9  from source, since it has to be linked to newer libraries than the system versions I have a script that starts gimp-2.9 that takes care of all the environmental variables, the script is in my $HOME/bin
```
#! /bin/bash

export INSTALL_PREFIX=$HOME/gimp-2.9

export PATH=$INSTALL_PREFIX/bin:$PATH
export LD_LIBRARY_PATH=$INSTALL_PREFIX/lib:$LD_LIBRARY_PATH

export PKG_CONFIG_PATH=$INSTALL_PREFIX/lib/pkgconfig:$PKG_CONFIG_PATH

$INSTALL_PREFIX/bin/gimp-2.9

```

I made it executable, made sure that it worked by running it to start gimp.


Now I made a .desktop file and placed it in ~/.local/share/applications
```
[Desktop Entry]
Type=Application
Terminal=false
Icon=/home/monkeybrain/share/icons/gimp.svg
Exec=gimp-2.9 %F
Name=GIMP-2.9
Categories=Graphics;



```

Since the script gimp-2.9 lives in $HOME/bin, it is directly in my path (see .bashrc) so I don't need to put in the full path in the Exec = line, if your script is elsewhere, put in the full path.
I made it executable,  clicked it and made sure that it indeed started gimp (by invoking the script gimp-2.9 in $HOME/bin)

Now either drag the .desktop file to the launcher from ~/.local/share/applications, or open the dash, find gimp and drag it to the  launcher, that's it.

---

### Post by Skaperen on 2018-04-08
the button is still not showing up. i've even rebooted a couple times.  here's what i have:

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Rumi
GenericName=Rumi
Comment=play rumi in the background
Icon=music
TryExec=/home/pdh/desktop/playrumi
Exec=/home/pdh/desktop/playrumi
```

```
drwxr-xr-x  28 root root  4096 Apr  4 23:44 /
drwxr-xr-x  26 root root  4096 Mar 23 20:53 /home
drwxr-xr-x 160 pdh  pdh  53248 Apr  8 20:10 /home/pdh
drwxr-xr-x   3 pdh  pdh   4096 May  9  2016 /home/pdh/.local
drwxr-xr-x  19 pdh  pdh   4096 Apr  5 20:30 /home/pdh/.local/share
drwxr-xr-x   2 pdh  pdh   4096 Apr  5 21:30 /home/pdh/.local/share/applications
-rwxr--r--   1 pdh  pdh    210 Apr  5 20:56 /home/pdh/.local/share/applications/playrumi.desktop
drwxr-xr-x   2 pdh  pdh   4096 Apr  5 21:12 /home/pdh/desktop
-rwxr--r--   1 pdh  pdh    117 Apr  5 21:07 /home/pdh/desktop/playrumi
```

/home2/magnatune was where i was testing logging out and back in.  /home/pdh is where it ultimately goes.  the script actually calls another script to execute a command in a background (detached) screen (the screen command) session, creating it if it does not exist, yet.  but, things can't even get that far since the button does not show up.  i can't click on it if it does not show up.

---

### Post by Skaperen on 2018-04-08
> **monkeybrain20122 said:**
> ??? !!!

I am not sure what you are doing, seems that you make the task very complicated for no reasons. Here is an example


what's complicated about it?  that it is running a shell script to play the music?

---

### Post by kerry_s on 2018-04-08
> [Desktop Entry]
Type=Application
Name=Rumi
Comment=play rumi in the background
Icon=music
Exec=/home/pdh/Desktop/playrumi
Categories=GTK;GNOME;AudioVideo;Player;Video;TV;


you just have a typo, fixed an simplified.
make sure to right click->properties->permissions & check the executable box. then click on it & select trust.

---

### Post by Skaperen on 2018-04-08
there are a couple terminal buttons, and entries there for them so a copied one with a name change.  i copied it with sed making the change so Unity would only see it with its new name and not have a chance to ever see it with a duplicate name.  then i logged out and back in.  it did not show up as a button.  so something else is needed to make buttons.

---

### Post by Skaperen on 2018-04-08
that other user name (*magnatune*) i did a test with before, i copied the terminal .desktop files from *pdh* (two work and a 3rd does not) to it, logged out, logged back in, and no new buttons.  then i noticed that the one terminal button *magnatune* has, there is no .desktop file in **[FONT=courier new]/home2/magnatune/.local/share/application[/FONT]**.  things are now even more strange about Unity.  maybe the change to Gnome is a good idea.

---

### Post by Skaperen on 2018-04-08
> **kerry_s said:**
> you just have a typo, fixed an simplified.
make sure to right click->properties->permissions & check the executable box. then click on it & select trust.

i don't see any typos.  the directory *desktop* (with a lower case 'd') is where the scripts really are.  is that what you thought was the typo?

```
lt1/forums /home/forums 9> ls -l /home/pdh/[dD]esktop
/home/pdh/Desktop:
total 0

/home/pdh/desktop:
total 8
-rwxr--r-- 1 pdh pdh 596 Apr  5 21:11 playmusic
-rwxr--r-- 1 pdh pdh 117 Apr  5 21:07 playrumi
lt1/forums /home/forums 10> 
```

---

### Post by Skaperen on 2018-04-08
> **monkeybrain20122 said:**
> BTW, you can check if your .desktop file is working by clicking it, if it works then you can just drag it from .local/share/applications to the launcher bar, that way you don't need to logout or login.

how do i click it if it does not show?

---

### Post by Skaperen on 2018-04-08
> **guber2 said:**
> @ Skaperen,
You may not be aware of this but your .desktop file does not need to be executable to work with the unity launcher.
If the file is correct you can drag and drop to the Unity launcher (sidebar).
However, if you want to test it by clicking on the actual .desktop in the file browser it needs to be executable.
If the .desktop file doesn't work , test your "Exec=" line in terminal, eg **/home2/magnatune/desktop/playrumi**

I usually make .desktop files in ~/.local/share/applications executable because they show differently in the file browser.
When executable the icon and name from the .desktop file is used.
eg Attached Pic shows the same .desktop file executable and non executable.

i did discover there are other .desktop files w/o executable and they work.  i took executable off mine, logged out, logged it, and it made no difference ... still no buttons for the new ones.

it does not show up in the file browser, either.  nothing in .local does.  maybe that's because of the dot hiding .local itself?  i've always wondered how the graphical utils handle that.  i'm used to typing -a or -A on *ls* or just using my *rls* command which ignores the leading dots.

---

### Post by monkeybrain20122 on 2018-04-08
.local/share/applications is a hidden folder, you open your file manager, press ctrl+h or choose "show hidden" from file manager's menu to show it. Everything that starts with a "." is hidden. Is that what you are asking, because I am not sure what you meant by you can't click .desktop file since it doesn't show.

---

### Post by Skaperen on 2018-04-08
> **monkeybrain20122 said:**
> I am not sure what you are asking, I suppose by "the button" you mean the launcher icon?  See Kerry_s's post for the template to make a .desktop file, and the Icon= line has to be supplied by you (point it to a jpg or png file that represents your script) then make the .desktop file executable, put it in ~/.local/share/applications and it will appear in the dash if you search for it (may need a logout/login) and once you find it then you can pin it to the unity launcher like you do with other applications. No, they don't get pinned there automatically and it makes sense, you don't want every single application you install to show up at the launcher, just the "quick launch" ones.

"button" is what i called things designated to be clicked on, when referring to that purpose.  that's why i used "button" in the title of the post that started the thread.  if i was referencing what is to be displayed i would refer to "icon".  other .desktop file examples have the line "Icon=music" so i used that.  for now, i would accept anything.

does it really need to be made executable?  one poster has said it does not.  two existing .desktop files w/o executable show up and work (my two terminal buttons).

what size does the icon need to be?  would .svg also work? should i just copy one from somewhere? where?

---

### Post by Skaperen on 2018-04-08
> **monkeybrain20122 said:**
> .local/share/applications is a hidden folder, you open your file manager, press ctrl+h or choose "show hidden" from file manager's menu to show it. Everything that starts with a "." is hidden. Is that what you are asking, because I am not sure what you meant by you can't click .desktop file since it doesn't show.

i don't normally use the file browser so i had no idea how to make it show hidden files.  i guess you don't normally use a terminal command line shell and as such didn't get my reference to how to show such files with *ls*.

---

### Post by monkeybrain20122 on 2018-04-08
> **Skaperen said:**
> "button" is what i called things designated to be clicked on, when referring to that purpose.  that's why i used "button" in the title of the post that started the thread.  if i was referencing what is to be displayed i would refer to "icon".  other .desktop file examples have the line "Icon=music" so i used that.  for now, i would accept anything.

does it really need to be made executable?  one poster has said it does not.  two existing .desktop files w/o executable show up and work (my two terminal buttons).

what size does the icon need to be?  would .svg also work? should i just copy one from somewhere? where?

Technically what is to be "clicked on" to launch a program is called a launcher, and as a file it is  called a .desktop file (Windows people tend to just call it an "icon") that's why I said after you made your .desktop file click on it to see if it launches the program (in this case by executing your script) At this point it doesn't have to be in  ~/.local/share/applications. But you move it there so that it can be picked up by the dash and the menu (if you use a menu addon or something, or if you use a different DE than unity which has a menu) There are three places where the system will find them:/usr/local/share/applications., /usr/share/applications and $HOME/.local/share/applications. Only the last one you can access without sudo and it works only on your account.

The "Icon =" in the .desktop file refers to a picture which you want the launcher/"button" to look like, you enter the path to a picture which you saved somewhere, png, jpg and svg all work. In my gimp example, Icon points to a .svg file I stored somewhere.

Yes, both the script and the .desktop file have to be executable.

---

### Post by monkeybrain20122 on 2018-04-08
> **Skaperen said:**
> i don't normally use the file browser so i had no idea how to make it show hidden files.  i guess you don't normally use a terminal command line shell and as such didn't get my reference to how to show such files with *ls*.

I get it, but in this instance you want to drag the .desktop file to the unity bar so that you can launch your script with a click, don't you? Just how do you do drag and drop and click a button with shell command??? If you are a cli exclusive person then you can just launch your script from the terminal, why bother with a button? Of course I know CLI and ls.

---

### Post by Skaperen on 2018-04-08
> **monkeybrain20122 said:**
> Then try run 

```
sudo updatedb
```

No it wouldn't work for a different user since the script and the .desktop files are both in your user's home

i would copy the files the same exact way on the new user.  at first i had the files on user *pdh*, then needed to try the logout/login thing but had 2 long running programs on user *pdh* and wanted to keep my place in some document reads.  so i copied everything over to user *magnatune* (normally used to browse [COLOR=#0000ff]magnatune.com[/COLOR] where i have a paid account) and tried the logout/login.  that was 3 days ago.  today, i can logout/login my main user *pdh* (and have done so 3 times this evening).  so far, nothing has gotten new buttons or icons to show up on the Unity launcher bar.

---

### Post by monkeybrain20122 on 2018-04-08
> **Skaperen said:**
> i would copy the files the same exact way on the new user.  at first i had the files on user *pdh*, then needed to try the logout/login thing but had 2 long running programs on user *pdh* and wanted to keep my place in some document reads.  so i copied everything over to user *magnatune* (normally used to browse [COLOR=#0000ff]magnatune.com[/COLOR] where i have a paid account) and tried the logout/login.  that was 3 days ago.  today, i can logout/login my main user *pdh* (and have done so 3 times this evening).  so far, nothing has gotten new buttons or icons to show up on the Unity launcher bar.

I have no idea why you need to test with a new user. I don't know what it is but you are doing something wrong.

---

### Post by Skaperen on 2018-04-08
sorry, i have been reading posts out of order, not expecting this thread to grow so long.  i will do better from now on.

---

### Post by Skaperen on 2018-04-08
> **monkeybrain20122 said:**
> I get it, but in this instance you want to drag the .desktop file to the unity bar so that you can launch your script with a click, don't you? Just how do you do drag and drop and click a button with shell command??? If you are a cli exclusive person then you can just launch your script from the terminal, why bother with a button? Of course I know CLI and ls.

people have been saying to have a .desktop file in ~/.local/share/applications.  should they have been saying more, like to drag it there?

dragging was not a specific factor of what i wanted.  my "want" is the end result.  if dragging achieves that, then fine, i'll do that. i just needed to know, plus how to get it to show up.  now i know and will try that, soon.  i'm waiting for replies to settle down on the thread right now.  i should go do some other project right now, like getting Ubuntu to see all my files in the AWS cloud.

i do already play my music with a command.  and running the script as a command also works.  before wanting it as a button, i would know whether or not i had started the screen session in a detached background or not.  but for this, i wanted to also verify if the screen session had been created and create one if not.  also, i wanted to cancel any previously playing music.  sending a ^C to that session would kill playing music or return non-zero if the *music* session did not yet exist.  the i could create it if needed and play the music.

```
lt1/forums /home/forums 13> cat /home/pdh/desktop/playmusic
#!/bin/bash
exec 0</dev/null
exec 1>/tmp/playmusic.out
exec 2>/tmp/playmusic.err
cd || exit 1
export PATH="/usr/local/bin:${PATH}"
sin -N music '^C'
if [[ $? != 0 ]] ; then
    sbg cols=184 rows=50 music
    sleep 0.125
    sin music '\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r'
    sin music '\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r'
    sin music '\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r'
fi
sin music time play "$@"
exit 0
lt1/forums /home/forums 14> cat /home/pdh/desktop/playrumi 
#!/bin/bash
exec 0</dev/null
exec 1>/tmp/playrumi.out
exec 2>/tmp/playrumi.err
exec /home/pdh/desktop/playmusic rumi
lt1/forums /home/forums 15>
```

the play command looks in the playlist.  *rumi* is in there.

---

### Post by monkeybrain20122 on 2018-04-08
> **Skaperen said:**
> people have been saying to have a .desktop file in ~/.local/share/applications.  should they have been saying more, like to drag it there?


No, you can easily move the .desktop file to .local/share/applications with shell command

```
 mv /desktop/file ~/.local/share/applications
```

or easier, just create it there
```
gedit ~/.local/share/applications/foo.desktop
```

Then perhaps with a logout/login the "button" will show up in your dash, from which you can just drag it to the launcher bar, or, just click it and then after it starts, pin it to the launcher bar. So there is one  drag and one click here, which I don't know how to express in shell commands,

But since you said you didn't want to login and logout, someone came along and said you could just drag the .desktop file from .local/share/applications to the Unity launcher bar without waiting for it to show up in the dash, so here is another drag and drop.

---

### Post by Skaperen on 2018-04-09
> **monkeybrain20122 said:**
> No, you can easily move the .desktop file to .local/share/applications with shell command

```
 mv /desktop/file ~/.local/share/applications
```

or easier, just create it there
```
gedit ~/.local/share/applications/foo.desktop
```

Then perhaps with a logout/login the "button" will show up in your dash, from which you can just drag it to the launcher bar, or, just click it and then after it starts, pin it to the launcher bar. So there is one  drag and one click here, which I don't know how to express in shell commands,

But since you said you didn't want to login and logout, someone came along and said you could just drag the .desktop file from .local/share/applications to the Unity launcher bar without waiting for it to show up in the dash, so here is another drag and drop.


i created it there by copying a saved template using *cp* then editing it with *emacs* (in the terminal).

the not wanting to logout/login applied to user pdh 3 days ago.  before i read about dragging it, i copied everything to user *magnatune* and did the logout/login there.  today (this evening) i have done logout/login 3 times on user *pdh* with no luck.  the last time was after making the playrumi.desktop file be the simplified one.

you mention "the dash".  is that another Unity term or GUI world term i need to learn.  is that the launcher bar?

i just ran that script on the command line:

```
lt1/pdh /home/pdh 8> desktop/playrumi
lt1/pdh /home/pdh 9>
``` 

of one of the seven terminal windows user *pdh* has open and am still listening to the music.

---

### Post by kerry_s on 2018-04-09
i think i know whats going on.

your trying to run a terminal based app without a terminal. you need to start a terminal that executes your terminal command.
example:
gnome-terminal -e /home/pdh/desktop/playrumi

so your launcher: rumi.desktop
 [Desktop Entry]
Type=Application
Name=Rumi
Comment=play rumi in the background
Icon=music
Exec=gnome-terminal -e /home/pdh/desktop/playrumi
Categories=GTK;GNOME;AudioVideo;Player;Video;TV;

---

### Post by Skaperen on 2018-04-09
> **kerry_s said:**
> i think i know whats going on.

your trying to run a terminal based app without a terminal. you need to start a terminal that executes your terminal command.
example:
gnome-terminal -e /home/pdh/desktop/playrumi

so your launcher: rumi.desktop
 [Desktop Entry]
Type=Application
Name=Rumi
Comment=play rumi in the background
Icon=music
Exec=gnome-terminal -e /home/pdh/desktop/playrumi
Categories=GTK;GNOME;AudioVideo;Player;Video;TV;

all that will be done when the button is clicked is that the script 1 will be run.  script 1 runs script 2.  script 2 passes a command string into a program that stuffs it into the keyboard input for a session of the screen command.  the first 2 scripts output nothing and do not need a terminal.  the shell running under screen has screen as its terminal emulator.

this does not explain why Unity is not placing it on the launch bar.

---

### Post by deadflowr on 2018-04-09
> you mention "the dash". is that another Unity term or GUI world term i need to learn. is that the launcher bar?

The dash is unity's menu system.
It's that pesky top icon in the launcher bar with the Ubuntu logo in it.

---

### Post by kerry_s on 2018-04-09
> **Skaperen said:**
> all that will be done when the button is clicked is that the script 1 will be run.  script 1 runs script 2.  script 2 passes a command string into a program that stuffs it into the keyboard input for a session of the screen command.  the first 2 scripts output nothing and do not need a terminal.  the shell running under screen has screen as its terminal emulator.

this does not explain why Unity is not placing it on the launch bar.

you make my head hurt. lol

so there are 3 scripts you want started from 1 launcher. why are there 3 scripts? can't you combine the scripts into 1?

can you post each script in code tags? that way these script geniuses we have here on the forums can rewrite/streamline your scripts into something usable as a launched app.
i'm old, my memory for programming is crap. i'm relearning since i got out the hospital but my minds just not what it use to be.

ill load ubuntu 16 into vm & see what it does with your code.

---

### Post by again? on 2018-04-09
> **kerry_s said:**
> you make my head hurt. lol


I feel your pain. ](*,)8-[

---

### Post by Skaperen on 2018-04-09
> **kerry_s said:**
> you make my head hurt. lol

so there are 3 scripts you want started from 1 launcher. why are there 3 scripts? can't you combine the scripts into 1?

can you post each script in code tags? that way these script geniuses we have here on the forums can rewrite/streamline your scripts into something usable as a launched app.
i'm old, my memory for programming is crap. i'm relearning since i got out the hospital but my minds just not what it use to be.

ill load ubuntu 16 into vm & see what it does with your code.

see post #36 for the scripts.  it's one code tag for both.

the 3rd is an existing command called "sin" (for "session input") that i wrote in _Python_ over a year ago.  it is part of a kit of 5 commands.  it is used a lot for many purposes.  "pulseaudio" in system mode seems to want a controlling tty.  running it under a background screen session achieves this.

the 2nd is a generic script coded in _bash_ the has the details of which screen session is used to play music (session "music"), how to create that session when it finds that it does not exist (command "sbg cols=184 rows=50 music"), how to stop current music being played (stuff in a ^C), and how to play the given music (command "sin music play ...").

the 1st (in _bash_)is a specific script for specific music.  if it turns out the button setup lets me include arguments then i can bypass the 1st script and won't need it.  if i do need it, there will eventually be one of these for each music i want to be able to play by button click (maybe 2 or 3).

---

### Post by kerry_s on 2018-04-09
```
lt1/forums /home/forums 13> cat /home/pdh/desktop/playmusic

```

```
#!/bin/bash
exec 0</dev/null
exec 1>/tmp/playmusic.out
exec 2>/tmp/playmusic.err
cd || exit 1
export PATH="/usr/local/bin:${PATH}"
sin -N music '^C'
if [[ $? != 0 ]] ; then
    sbg cols=184 rows=50 music
    sleep 0.125
    sin music '\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r'
    sin music '\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r'
    sin music '\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r'
fi
sin music time play "$@"
exit 0
```

```
lt1/forums /home/forums 14> cat /home/pdh/desktop/playrumi 

```

```
#!/bin/bash
exec 0</dev/null
exec 1>/tmp/playrumi.out
exec 2>/tmp/playrumi.err
exec /home/pdh/desktop/playmusic rumi
lt1/forums /home/forums 15>
```

so those are the scripts/commands i see from post #36

i'm thinking why? your only playing music from a folder right? why the need for the scripting? there are easier ways.
just off the top off my head with what i have installed, i would just:
mpv /path/to/my/music/*

done, plays everything in that folder. i just don't get why your doing it in such a complicated way.

---

### Post by mc4man on 2018-04-11
As has been mentioned previously the easiest way to add is to ,
Go to wherever you can actually see the .desktop file. Pick it up with your cursor and drop on to the unity launcher.
There are 2 possible results
1. It is added where you dropped it in the launcher
2. It disappears

If it disappears then there is a issue with the .desktop file that makes it unsuitable to use in the unity launcher. This 'issue' is almost always that the Exec= line has a problem. Generally the issue would be that the Exec='s target can't be found or the target isn't executable. Period.
(- only other possibility is a malformed Exec= line itself.

The launcher does not access whether the Exec= target will run, work,  whatever. Just whether it exists & can be executed.

---

### Post by Skaperen on 2018-04-11
> **kerry_s said:**
> ```
lt1/forums /home/forums 13> cat /home/pdh/desktop/playmusic

```

```
#!/bin/bash
exec 0</dev/null
exec 1>/tmp/playmusic.out
exec 2>/tmp/playmusic.err
cd || exit 1
export PATH="/usr/local/bin:${PATH}"
sin -N music '^C'
if [[ $? != 0 ]] ; then
    sbg cols=184 rows=50 music
    sleep 0.125
    sin music '\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r'
    sin music '\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r'
    sin music '\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r'
fi
sin music time play "$@"
exit 0
```

```
lt1/forums /home/forums 14> cat /home/pdh/desktop/playrumi 

```

```
#!/bin/bash
exec 0</dev/null
exec 1>/tmp/playrumi.out
exec 2>/tmp/playrumi.err
exec /home/pdh/desktop/playmusic rumi
lt1/forums /home/forums 15>
```

so those are the scripts/commands i see from post #36

i'm thinking why? your only playing music from a folder right? why the need for the scripting? there are easier ways.
just off the top off my head with what i have installed, i would just:
mpv /path/to/my/music/*

done, plays everything in that folder. i just don't get why your doing it in such a complicated way.
to me it is a simple way.  i think this issue is that you don't know the goals.

i want it to be compatible with how i play music by command line.  i doubt if *mpv* knows how to stop music that is already playing by my command line.  i also doubt if it knows anything about my playlists that i have been using for years.  and i doubt if it knows anything about my play speed system.

the scripts have a logical separation of roles.  having each script for different music be coded with a the details of how to play music  but if the .desktop lets me code arguments, then i can have each configuration run the 2nd script, passing it the name of the playlist (different for each button).

---

### Post by kerry_s on 2018-04-11
actually mpv has like 720 options last i checked. but that's beside the point your already use to what your use to.
anyways, doesn't matter what i think. i'd like you to attain your goal.

launchers are simple. they just point to a executable. so if your executable can run with out issues, in theory it should just work.
a: your dealing with several scripts
b: there not gui based

be right back

---

### Post by Skaperen on 2018-04-11
> **mc4man said:**
> As has been mentioned previously the easiest way to add is to ,
Go to wherever you can actually see the .desktop file. Pick it up with your cursor and drop on to the unity launcher.
There are 2 possible results
1. It is added where you dropped it in the launcher
2. It disappears

If it disappears then there is a issue with the .desktop file that makes it unsuitable to use in the unity launcher. This 'issue' is almost always that the Exec= line has a problem. Generally the issue would be that the Exec='s target can't be found or the target isn't executable. Period.
(- only other possibility is a malformed Exec= line itself.

The launcher does not access whether the Exec= target will run, work,  whatever. Just whether it exists & can be executed.

i see the file in my command line terminal.  there is no means to "pick it up".  the Exec= is correct with the exact path of the script to execute.  the .desktop file exists and is executable.  so i need to run/use a graphical file browser?  what changes in the file system so that the button shows up at next login (even after a reboot)?

the scripts are in a subdirectory named "desktop" which has a lower case 'd'.  this is separate from the subdirectory named "Desktop" which has an upper case 'D'  both exist.

```
lt1/forums /home/forums 5> cat /home/pdh/.local/share/applications/playrumi.desktop
[Desktop Entry]
Type=Application
Name=Rumi
Comment=play rumi in the background
Icon=music
Exec=/home/pdh/desktop/playrumi
Categories=GTK;GNOME;AudioVideo;Player;Video;TV;
lt1/forums /home/forums 6> cat /home/pdh/desktop/playrumi
#!/bin/bash
exec 0</dev/null
exec 1>/tmp/playrumi.out
exec 2>/tmp/playrumi.err
exec /home/pdh/desktop/playmusic rumi
lt1/forums /home/forums 7> cat /home/pdh/desktop/playmusic
#!/bin/bash
exec 0</dev/null
exec 1>/tmp/playmusic.out
exec 2>/tmp/playmusic.err
cd || exit 1
export PATH="/usr/local/bin:${PATH}"
sin -N music '^C'
if [[ $? != 0 ]] ; then
    sbg cols=184 rows=50 music
    sleep 0.125
    sin music '\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r'
    sin music '\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r'
    sin music '\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r\r'
fi
sin music time play "$@"
exit 0
lt1/forums /home/forums 8>
```

---

### Post by Skaperen on 2018-04-11
i copy and paste from my shell terminal showing the command line, such as "cat ${filename}" so people can see exactly how i got that output, what th exact file names are, etc.  then i put that in code tags.

---

### Post by kerry_s on 2018-04-11
lost my chain of thought.
i don't know if your scripts work, then a desktop file should execute it.

i just created 1 to max the volume on click, cause it resets to 100% after reboot/startup. it works with just a click.
```

[Desktop Entry]
Type=Application
Name=Sound Max
Comment=Boost sound
Icon=sound
Exec=pactl -- set-sink-volume 0 150%
Categories=GNOME;


```

---

### Post by mc4man on 2018-04-11
> **Skaperen said:**
> i copy and paste from my shell terminal showing the command line, such as "cat ${filename}" so people can see exactly how i got that output, what th exact file names are, etc.  then i put that in code tags.
As the trouble to use a cursor is too much, the short & sweet of it

```
gsettings get com.canonical.Unity.Launcher favorites
```

Take value returned inc. the brackets, add your .desktop to that value in position in launcher desired ( any place before 'unity://running-apps',), then use the gsettings set command to use the new value. If .desktop added is not in a applications folder in the launchers 'path' so to speak, then add that .desktop with it's path.
Additionally add quote marks  before & after brackets  of the intended value.

An ex. of adding a .desktop that requires adding path, i.e one Not in an applications folder.
current here
>  gsettings get com.canonical.Unity.Launcher favorites
['application://nemo.desktop', 'application://firefox.desktop', 'application://utility.desktop', 'application://org.gnome.Terminal.desktop', 'application://gimp.desktop', 'application://mpv.desktop', 'unity://running-apps', 'unity://expo-icon', 'unity://devices']

Adding a .desktop that's sitting on the Desktop (vlc.desktop) to a position under mpv
>  gsettings set com.canonical.Unity.Launcher favorites "['application://nemo.desktop', 'application://firefox.desktop', 'application://utility.desktop', 'application://org.gnome.Terminal.desktop', 'application://gimp.desktop', 'application://mpv.desktop', [COLOR="#0000CD"]'application:///home/doug/Desktop/vlc.desktop',[/COLOR] 'unity://running-apps', 'unity://expo-icon', 'unity://devices']"

---

### Post by Skaperen on 2018-04-13
> **kerry_s said:**
> lost my chain of thought.
i don't know if your scripts work, then a desktop file should execute it.

i just created 1 to max the volume on click, cause it resets to 100% after reboot/startup. it works with just a click.
```

[Desktop Entry]
Type=Application
Name=Sound Max
Comment=Boost sound
Icon=sound
Exec=pactl -- set-sink-volume 0 150%
Categories=GNOME;


```

this tells me that Exec= in a .desktop file can handle command arguments.  i've seen things in the past that cannot.  i would have eventually tested this but now i don't need to.  i can have each Exec= in each .desktop file just run the 2nd script and pass the name of the playlist right there.  the 1st script (a different one for each playlist i want to create) is no longer needed.

---

### Post by Skaperen on 2018-04-13
@mc4man i need to come back later and re-read this and try it.

---

### Post by again? on 2018-04-13
> **Skaperen said:**
> this tells me that Exec= in a .desktop file can handle command arguments.  i've seen things in the past that cannot.  i would have eventually tested this but now i don't need to.  i can have each Exec= in each .desktop file just run the 2nd script and pass the name of the playlist right there.  the 1st script (a different one for each playlist i want to create) is no longer needed.

[desktop-entry-spec/#exec-variables]("https://developer.gnome.org/desktop-entry-spec/#exec-variables")

---

### Post by Skaperen on 2018-04-18
> **guber2 said:**
> [desktop-entry-spec/#exec-variables]("https://developer.gnome.org/desktop-entry-spec/#exec-variables")

ooh, documentation i have wanted.  but i would not have looked around Gnome stuff for it.  is Unity really a Gnome creation?

a quick look through the whole thing and i see nothing related to how to make the button show up other than the idea not to use "hidden".

---

### Post by again? on 2018-04-18
Unity is a graphical shell for the GNOME desktop environment in much the same way as gnome-shell is.
Unity was created by Canonical as a plugin for the compiz window manager.
Even though the unity launcher implements it's own style(eg quicklists) it still relies on the gnome desktop specs.
[https://en.wikipedia.org/wiki/GNOME#History](https://en.wikipedia.org/wiki/GNOME#History)

---

### Post by again? on 2018-04-19
> **Skaperen said:**
> ooh, documentation i have wanted.  but i would not have looked around Gnome stuff for it.  is Unity really a Gnome creation?

a quick look through the whole thing and i see nothing related to how to make the button show up other than the idea not to use "hidden".
Repeat from mc4man....
> **mc4man said:**
> As has been mentioned previously the easiest way to add is to ,
Go to wherever you can actually see the .desktop file. Pick it up with your cursor and drop on to the unity launcher.
There are 2 possible results
1. It is added where you dropped it in the launcher
2. It disappears

If it disappears then there is a issue with the .desktop file that makes it unsuitable to use in the unity launcher. **This 'issue' is almost always that the Exec= line has a problem**. Generally the issue would be that the Exec='s target can't be found or the target isn't executable. Period.
(- only other possibility is a malformed Exec= line itself.

The launcher does not access whether the Exec= target will run, work,  whatever. Just whether it exists & can be executed.

....and if the desktop file is executable and the syntax is correct this command will run it....
```
xdg-open [COLOR="#696969"]*/path/to/your/.desktop*[/COLOR]
```

There is also ...
```
desktop-file-validate [COLOR="#696969"]*/path/to/your/.desktop*[/COLOR]
```
but this will not verify your actual Exec line though.

A simple way to check if it's your Exec line is to change it to launch an app like...
```
Exec=/usr/bin/gedit
```

---

