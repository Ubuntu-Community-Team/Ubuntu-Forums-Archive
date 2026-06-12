---
title: "startup scripts"
date: 2012-08-03
forum: Desktop Environments
---

### Post by lostinspaces on 2012-08-03
Hi, 
First off I am new to these forums, and new to ubuntu / linux. I have followed the forums and setup my system, but what I want to do is create a script for when my computer first starts to copy a file (playlist or presentation) and overwrite the old file, then play it. 
I've done this in Windows, but I am completely lost in this OS. 
 
Could someone direct me to the information so I can have a script run on startup please. 
 
Thanks

---

### Post by hakermania on 2012-08-03
**Welcome to the forums!**

Stay calm and follow my instructions :)

Do you know how to create your script? If no, then open the 'Text Editor' (called Gedit) and start a new document with
```

#!/bin/bash

```
as the first line. Then, after the 1st line, you can place your commands.
You can use the command 'cp' so as to replace the old file (which will be replaced with no problem, it will not prompt if the file already exists).

Then you can open the playlist you want to play with VLC (or any other player you prefer) after a certain timeout (10-15 seconds so as to let the system load anything it has to load).

So, the script should go something like this:
```

#!/bin/bash
cp ~/playlist_new ~/playlist_old #replace the old playlist with the new, the '~' stands for /home/yourusername
sleep 15 #sleep 15 seconds

vlc ~/playlist_old #launch your favorite media player with the selected playlist!

```
Now, after writing the above to a text editor like Gedit, save your file to your preferable location (most users tend to place their scripts under ~/Documents or under ~/bin). So as to be easier for you to distinguish that this is a shell script give it the extension .sh (example: launch_playlist.sh).

After saving the file, right click on it, go to Properties->Permissions and tick the 'Allow executing file as program'.

You are almost done with your script. In order to have it running on startup you need to do something simple: To create a launcher and place it to the appropriate directory.

Head to ~/.config/autostart/ If the 'autostart' directory doesn't exist, then create it.

Then, create there a file named anythingyouwant.desktop with the below contents:
```


[Desktop Entry]
Type=Application
Exec=/home/alex/Documents/myscript.sh
Terminal=False
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=Copy playlist
Name=Copy playlist

```

Edit the above fields so as to match your needs and you are done!

---

### Post by lostinspaces on 2012-08-03
thank you. I will reply if I have problems
 
EDIT: I cannot save the script in /bin folder as I do not have permission.

---

### Post by lostinspaces on 2012-08-07
saved the file in documents, completely unable to navigate to ~.config folder. did it once. no idea what I did to get there now but I had managed to make the little pleasure boxes of directory structure turn into an address bar and I typed the info in. This little feat has stopped me from repeating it. 
 
EDIT: Figured out the LOCATION trick through a combination of rage, frustration and determination.
 
EDIT2: When I first tried to run the file it prompted me that playlist_old didn't exist so I made one but it doesn't seem like the script is working as intended. There is no dialogue box that comes up on boot, and nothing actually starts.  
 
One thing that I did based off an assumption is that for the .desktop file, I made it in gedit then saved it into documents then copied it into the autostart directory.

---

### Post by hakermania on 2012-08-08
Ooops, sorry for not including all these information in my initial answer, but your question didn't ask many things, as well, so I wasn't sure what you did know and what you didn't know...

Well, in order to navigate to the .config folder, open your home directory (where you can see the folders Music, Downloads, Documents etc). Then, hit Ctrl+H in order to reveal the hidden files (the hidden files begin with a dot (.) and nautilus hides them by default for making it easier to you to navigate to the most basic folders of your home directory, like Music and Videos).

Then, find and double click on the .config folder. After going into there, if an 'autostart' folder doesn't exist, then create it (right click->create new folder and name it autostart). Inside the autostart directory you have to place a .desktop file pointing to your script.
This is another .desktop file example:
```

[Desktop Entry]
Type=Application
Name=Copy playlist
Exec=/home/username/Documents/myscript.sh
Terminal=false
Comment=Copy and play the playlist
Categories=Utility;Application;

```
Edit the following field so as to match your needs:
*Exec: where is the script you created? Point to that script. Instead of 'username' in the above example, place your username, example: alex or jhon*

Now, let's talk about the script. I will call it myscript.sh and I will place it at ~/Documents/myscript.sh (NOTE: ~ means **/home/username**, example: **/home/alex**)

These are the contents of myscript.sh, always based on what you requested from your initial post:
```

#!/bin/bash
# 1) Copy the new playlist over the old playlist
cp ~/playlist_new ~/playlist_old
# 2) Sleep 15 seconds so as the system to completely boot
sleep 15 
# 3) Play the overwritten old playlist with your favorite media player
vlc ~/playlist_old

```

Let's analyze it a bit:
1) The command 'cp' copies the /home/username/playlist_new to /home/username/playlist_old, so, after the 'cp' command executes, you will have 2 identical files to your /home/username/ directory:
playlist_new and playlist_old will be the same files.

2) Then, we just sleep for 15 seconds, we let the system load completely what it has to load, before doing a hard task like opening the playlist and start playing it.

3) Play the playlist with your favorite player.

What you have to be careful of:

a) Be careful of the paths of the playlist_new and the playlist_old, as you understand, you have to edit the above script so as to point to valid playlist_new and playlist_old files, the above script is just an example. For example, if your playlists are at ~/Documents/playlist_old.m3u and ~/Documents/playlist_new.m3u, you have to add these paths there, instead of ~/playlist_old and ~/playlist_new, correspondingly.

b) Don't forget, after saving the myscript.sh to ~/Documents/ to give it executable rights: Right click on it->Properties->Permissions->Allow executing file as program.

c) In general, you have to understand that the above is a simple example, rather general, and you have to edit the paths so as to much your needs.

---

### Post by lostinspaces on 2012-08-08
First off, thanks for your help and your patience. 
 
I am confident that I've created the .sh file correctly, using the correct paths and filenames.  (I typed out the whole thing here but the page timed out)
 
I believe my problem is because I need to make the .desktop file stored in the autostart folder, to be trusted. 
 
 
If I doubleclick the .desktop file I receive the error
 
Untrusted application launcher
The application launcher "playstart.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe

---

### Post by hakermania on 2012-08-08
> **lostinspaces said:**
> First off, thanks for your help and your patience. 
 
I am confident that I've created the .sh file correctly, using the correct paths and filenames.  (I typed out the whole thing here but the page timed out)
 
I believe my problem is because I need to make the .desktop file stored in the autostart folder, to be trusted. 
 
 
If I doubleclick the .desktop file I receive the error
 
Untrusted application launcher
The application launcher "playstart.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe

I don't think that this is the case, you get this error because the .desktop file doesn't have executable permissions, but it doesn't really have to in your situation (in order to start on startup). 

But, in any case, in order to solve this problem, right click on the file->Properties->Permissions->Allow executing file as program and you should be done with this as well...

---

### Post by lostinspaces on 2012-08-08
> **hakermania said:**
> I don't think that this is the case, you get this error because the .desktop file doesn't have executable permissions, but it doesn't really have to in your situation (in order to start on startup). 
 
But, in any case, in order to solve this problem, right click on the file->Properties->Permissions->Allow executing file as program and you should be done with this as well...
 
Once I had changed the permissions on the .desktop file it changed it's icon and name to Copy playlist. 
I ran the file and found that it was searching for the wrong name (playlist1 instead of playlist0)
For reference the .sh file had this line 
cp ~/Documents/playlist1.m3u ~/Documents/playlist0.m3u
 
and 
vlc ~/Documents/playlist1.m3u
 
I have renamed my existing playlist file to playlist1.m3u and changed the vlc line to
vlc ~/Documents/playlist0.m3u
 
I now can execute the Copy Playlist file in the autostart folder and it duplicates the file and executes the copied playlist. 
 
However, on reboot it does not start up.
 
 I see that I forgot to mention I am using Ubuntu 12.04 if that has any affect on this problem.

---

### Post by lostinspaces on 2012-08-08
I just wanted to say THANKS!!!!
I've managed to get it working now. I will update this tomorrow with my process, but what needed to be done was a format and reinstallation of ubuntu.

---

### Post by hakermania on 2012-08-08
> **lostinspaces said:**
> I just wanted to say THANKS!!!!
I've managed to get it working now. I will update this tomorrow with my process, but what needed to be done was a format and reinstallation of ubuntu.

Hey, good thing that you figured that out! Looking forward to hearing from you :)

---

### Post by lostinspaces on 2012-08-09
> **hakermania said:**
> Hey, good thing that you figured that out! Looking forward to hearing from you :)
 
OK so after the format I created a folder under my user named bin. I created the .sh file as you described and stored it in that folder marking it as executable.
 
#!/bin/bash
cp ~/Documents/playlist0 ~/Documents/playlist1
sleep 15
vlc ~/Documents/playlist1
 
I then created the autostart directory in .config and made a .desktop file with this;
 
[Desktop Entry]
Type=Application
Name=Copy playlist
Exec=/home/USER/bin/playstart.sh
Terminal=false
Comment=Updates playlist
Categories=Application;
 
I removed the Utility variable from Categories as it showed up blocked in red, which I figured meant incorrect. 
 
I did not need to mark it as executable, everything worked as expected on reboot. :D
 
Because this is just one part of my project, I was planning on adding more lines to the .sh file to perform other basic actions. I'm assuming that it's better to localize everything within the one script rather than running multiple scripts and loaders. 
 
Thanks again!

---

