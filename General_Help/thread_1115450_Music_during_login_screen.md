---
title: "Music during login screen"
date: 2009-04-03
forum: General Help
---

### Post by enabulator on 2009-04-03
Does anyone know if it is possible to run music during the login screen (not just after you login?)

Even if it's not implemented standardly, if only with a script or something. . .

thanks

---

### Post by mb_webguy on 2009-04-03
System->Administration->Login Window, Accessibility tab.  Change the "Login screen ready sound".  I'm pretty sure it has to be a wav.

---

### Post by damis648 on 2009-04-03
Currently a drum tone plays at the login screen, you can change it with System>Administration>Login Window.:popcorn:

---

### Post by enabulator on 2009-04-03
Thanks! Any chance that I can have a playlist? I guess I could just make a really long sound with different songs.

do you happen to know if it was a really long sound, would it stop when I log in, or would it keep going until finished?

EDIT: It doesn't stop - anyone know to make it stop?

---

### Post by enabulator on 2009-04-04
Is there any way to have some script or something run when it get to the login screen that plays music, and then have something of a similar nature (script or something) run when you log in to stop the music?

---

### Post by mocoloco on 2009-04-04
Not sure but poke around in /etc/gdm  maybe the file /etc/gdm/init/Default to start with.  Stick a command in there to play a file (found a good resorce for [CLI audio players]("http://www.linux.com/feature/124907")) and see what happens. If that doesn't do it look at the other files in there.
Of course back up anything you change first.

Once you know that works find something that will do a whole playlist.

---

### Post by enabulator on 2009-04-04
Thanks for the reply,

I'm new to ubuntu, and I don't know bash, or whatever the files are coded in. Sometime i might learn, but at least now I have an idea of where to start.

EDIT: the /bin/sh means its dash, right?

---

### Post by enabulator on 2009-04-04
is dash/bash/whatever it is basically the same as typing in the terminal?

---

### Post by enabulator on 2009-04-04
ok, so I got music to play with
```
mplayer /path/to/file
```
However, I didn't get quite what I wanted.

If I add the command to /etc/gdm/Init/Default, it playes before the login screen, and the song has to finish before the screen comes up at all.
If I add to /etc/gdm/PreSession/Default, It plays after I login, but before the things under System >> Preferences >> Sessions run.
I am assuming that if I add to /etc/gdm/PostSession/default, that it will run after the things under System >> Preferences >> Sessions run.
If I add to /etc/gdm/PostLogin/Default.sample, it doesn't do anything (even if name changed to Default) - btw:why?

For all of these all action stops, the music plays, and then it continues. Can the music run concurrently with whatever else is happening?

I still don't even know how to have the music stop after someone logs in.

Does anyone else have any other ideas on where to go with this? Is it impossible?

thanks

---

### Post by dcstar on 2009-04-04
> **enabulator said:**
> ok, so I got music to play with
```
mplayer /path/to/file
```
However, I didn't get quite what I wanted.

If I add the command to /etc/gdm/Init/Default, it plays before the login screen, and **the song has to finish** before the screen comes up at all.
.......

```
mplayer /path/to/file **&**
```

---

### Post by mocoloco on 2009-04-05
dcstar's answer will let it start playing and not wait to finish.  As far as stopping it, a quick and dirty way would be to add this command to /etc/gdm/PreSession/Default so that it will run right after you log in:
```
killall mplayer
```

That's not the cleanest way because it could kill something you may want if someone else is logged in already, and both that and how you're starting it might not do what you want if you have multiple users logged in.  But it's a start :)

---

### Post by enabulator on 2009-04-06
If I do what David says, 
```
mplayer /path/to/file &
```
Then the music starts to play, followed by the login screen coming up. The login screen comes up during the music - not quite at the same time, but ok.

Is there any way to reference the process/task/whatever is playing the music so that I can tell it to stop from the /etc/gdm/PostLogin/Default file, so that it stops when I log in? Better yet, have a script or something run to decrease the volume to get a fade out effect?

EDIT: Didn't see reply above, still not ideal though. . .

---

### Post by enabulator on 2009-04-06
Is there something that can be done with PIDs? Record to a file? read later to tell what to kill? I'm new, so I'm not even sure what they are.

---

### Post by enabulator on 2009-04-06
If you have a more elegant solution, in either sound quality, or functionality quality, please tell me.

What I have now:
 - mplayer path/to/file1 &           in /etc/gdm/Init/Default (to play login music)

 - killall mplayer
  (next line) mplayer path/to/file2 &      in/etc/gdm/PostLogin/Default (to stop login music and play music after I login) - I supppose that this line may not be necessary, because there there is a 'login sucessful' option thing that might work, too

(EDIT: it works, )However, then I get problems with running sound files:
-run via mplayer - Error:[AO_ALSA] Unable to set hw-parameters: -Input/output error
-via gnusound -  makes X crash? (it sends me to the login screen)
-flash sound doesn't work
-stuff the the effect of audio device missing/not found/busy

is something running/locking a audio device?

thanks

EDIT - line mentioned above may be necessary so that I get the right order (First music shuts off before second starts)

---

### Post by enabulator on 2009-04-06
If it makes any difference, if I
```
sudo /etc/init.d/alsa-utils restart
```
i get:
 * Shutting down ALSA...                                                        amixer: Invalid command!
                                                                         [ OK ]
 * Setting up ALSA...                                                    [ OK ] 

I can also go
```
sudo /etc/init.d/pulseaudio restart
```
which doesn't print anything

It still doesn't work afterwards.

---

### Post by mocoloco on 2009-04-08
I didn't mean to imply that using the mplayer command was the best solution, just a means to see if you were putting the command in the right place to have it start at the right time.
I think you're going to need to write some sort of script that will start a command line media player, one that can do playlists, and can be properly stopped at the right time.  Look at the link in my first post in this thread which mentions some possible player options.  You may have to find out how to put the player in the background, then bring it to the foreground to stop it, etc.

---

### Post by enabulator on 2009-04-08
Thanks for your help,

What do you mean by 'command line'? the command mplayer doesn't bring up a GUI, although it does allow interactive keyboard input from the terminal.

Is something with more fine control needed, or did you just think that mplayer brought up a gui?

EDIT: I don't quite get where you are coming from. . .

---

### Post by mocoloco on 2009-04-08
[http://en.wikipedia.org/wiki/Command_line]("http://en.wikipedia.org/wiki/Command_line")  :)  

I'm saying you're using exactly the type of app you should, but as you noticed, when you run the command either at a prompt or in a script it waits for it to finish before it runs the next command, unless you put it to the background by adding "&" after the command.  I believe there are CLI apps that will follow a playlist and one like that you could start in the background, or have it run as a [daemon]("http://en.wikipedia.org/wiki/Daemon_(computer_software)").  Don't know for sure cause I haven't used any, but I'm sure a little googling would be beneficial.
The more you learn, the more fun it gets :)

---

