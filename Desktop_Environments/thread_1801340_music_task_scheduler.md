---
title: "music task scheduler"
date: 2011-07-10
forum: Desktop Environments
---

### Post by rkanth on 2011-07-10
First of all, let me clarify to moderators that I posted this request in "Absolute Beginner Talk" and re-posting here; I don't know how to remove that post. I need help with this:

I used to use Karmic and have moved to Lucid a day ago.
One feature I enjoyd was the way ubuntu played music everyday at 5.05 am to wake me up. I remember using gnome-scheduler for this and some help from guys here.

1. The playlist file is on my desktop in a folder named "Music Playlists". The music files in the playlist are in home/music folder.

2. In the command box in the scheduler right now there is one "ls". Can somebody tell me what command to type in there? Should I specify a music player, please tell me how to do it. All files are mp3.

Even if somebody tells me how to schedule a music player play a list of songs at a given time daily by any other way(need not be by gnome-scheduler) on Ubuntu 10.04, It will be helpful.

RK

---

### Post by Toz on 2011-07-10
What media/music player do you use?

You could run a command line player (mpg321) to do this. A command like:```
gnome-terminal -x mpg321 -Z ~/music/*
```will open a terminal window and start playing the contents of ~/music (home/music) randomly. 

You will need to have mpg321 installed. Find it in the Software Centre or: ```
sudo apt-get install mpg321
```

Since I use Xubuntu and don't have gnome-terminal installed, try it now from a terminal window to see if it works.

You can put the command **/usr/bin/gnome-terminal -x /usr/bin/mpg321 -Z /home/<your_user_id>/music/*** (replace the <your_user_id> string with your userid) in gnome-scheduler 

_or_ use the built-in crontab functionality.

```
crontab -e
```
scroll down and append at the end of the file:
```
5 5 * * * /usr/bin/gnome-terminal -x /usr/bin/mpg321 -Z /home/<your_user_id>/music/*
```

Ctrl-O (that's O as in Oscar) to save and Ctrl-X to exit.

As per that crontab entry, the music will start to play at the 5th minute of the 5th hour (24 hour clock) of every day.

---

### Post by rkanth on 2011-07-10
Thank you Toz. Much appreciated.

---

