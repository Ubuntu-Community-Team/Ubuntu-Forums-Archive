---
title: "Timely Jobs/ Script Help Anyone?"
date: 2004-12-26
forum: Desktop Environments
---

### Post by ankitmalik on 2004-12-26
Hi

I am an intermediate user and usually listen to songs through the command line.
I do it like this

Run gnome-terminal first

$ cd Music
$ cd V*
$ mplayer song.extension

What I want to ask is is there a script which I can make [thru someone's help as I am alien to it!] which will replace the three commands with a single word!

Eg.

$ music 


Second thing i want to ask is

Due to special reasons i have to uninstall an app @ a specific time of the day and then install it later @ another specific time

For example everyday @ 9 in the morning I do this

# apt-get remove package

and @ 9 in the evening I do this

# cd /var/cache/apt/archives
# dpkg -i package

Now is there a script possible/ app possible which can do this automagically for me without my intervention and in the background if possible? I think there is something called cron for this but I am not sure.

Can anyone help me? Thanks in Advance!

---

### Post by ahyden on 2004-12-27
[QUOTE=ankitmalik]Hi

I am an intermediate user and usually listen to songs through the command line.
I do it like this

Run gnome-terminal first

$ cd Music
$ cd V*
$ mplayer song.extension

What I want to ask is is there a script which I can make [thru someone's help as I am alien to it!] which will replace the three commands with a single word!

Eg.

$ music 
[/QUOTE]
Hey

You can create a simple shell script for that:
Create a new file with the name you want, e.g.
gedit music
At the top of the file, write this:
#!/bin/bash

This tells the intepreter to use bash, which is the program that is used to intepret the commands you type in the console.
Then write the commands you want, so your script would look something like this:

#!/bin/bash
cd Music
cd V*
mplayer song.extension

save and close gedit and type (in the console):
chmod +x music

this will make the script music executable, so you can run it.

Now you should be able to run it by typing ./music and it will run the commands inside the script.

If you want to know more about bash and scripting, here is a guide:
[http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal) 

[QUOTE=ankitmalik]
Second thing i want to ask is

Due to special reasons i have to uninstall an app @ a specific time of the day and then install it later @ another specific time

For example everyday @ 9 in the morning I do this

# apt-get remove package

and @ 9 in the evening I do this

# cd /var/cache/apt/archives
# dpkg -i package

Now is there a script possible/ app possible which can do this automagically for me without my intervention and in the background if possible? I think there is something called cron for this but I am not sure.

Can anyone help me? Thanks in Advance![/QUOTE]

You are right, this can be done with cron, by editing /etc/crontab.
You can learn more about it by typing man crontab or check this tutorial 
[http://www.clockwatchers.com/cron_main.html](http://www.clockwatchers.com/cron_main.html)

There is a graphical tool called gcrontab which may make it easier. Install it with:
sudo apt-get install gcrontab
and then start it by typing gcrontab in the console

Good luck :)

---

### Post by ahyden on 2004-12-27
I'm a bit tired, but when I reread the script you wanted I figured you want to be able to type the name of the song to play, e.g. music song1.mp3

This simple script should work

#!/bin/bash
cd directory/with/music
mplayer $1 &

$1 is the first word you type after the script, so ./music song1.mp3 would do this
cd directory/with/music
mplayer song1.mp3 &

The & will put mplayer to the background so you can continue typing in the same console after executing the script.

---

### Post by ankitmalik on 2004-12-27
Hi 

Thanks a lot ! It works!

Now Ok wanting to push it just a bit more

I like that it goes to /home/user/Music/Ve* and then plays a particular song!

But can it be morphed so that it asks me which song to play eg

$ music
Enter the song you wanna play > lak*.rm
Now playing lak..... ! Enjoy! 
________________________-

Thanks in advance

---

### Post by ahyden on 2004-12-27
Well you can use the script I posted last to enter the file to play like this:
./music song1.mp3

Or if you want it to ask you, this should work:

#!/bin/bash
cd /dir/to/music
echo -n "Enter the song you wanna play >"
read ANSWER
echo Now playing $ANSWER Enjoy!
mplayer $ANSWER &

Edit: corrected script :)

---

### Post by ankitmalik on 2004-12-27
Thanks!

Will try out
You are a gr8 help

---

### Post by ankitmalik on 2004-12-27
IT Works yet again though this time with a correction!

It should be mplayer $ANSWER &

But thanks

how about stretching it further thanks to your expertise!

a) Ask for $ANSWER
b) Search for $ANSWER in the subfolders and the folder
c) Play the closest match to $ANSWER???

---

### Post by Artiom on 2004-12-28
I'm sorry if will be rude but ahyden gave you more then needed, so you can continue to add more features to it.

show some effort  :mrgreen: 

post what you tryed

---

### Post by ankitmalik on 2004-12-28
I know I did but I am a ZERO in shell scripting.

Although thanks to ahyden I could make this, I cant proceed any further as I dont know the commands !

Whatever he thought me, using that, I have made a script which can automagically set 40 players in Supertux! I have named it Supercrack!

So Supercrack anyone???

---

### Post by ankitmalik on 2004-12-29
Ok Ok!

I now have something to give back to Ubuntu [nothing big, actually very minute!]
I have just started with Shell Scripting thanks to ahyden and I have now made a very simple script for installing Mplayer on Ubuntu.

This is thanks to the Ubuntu Multimedia HOWTO. I have used those commands but now the script does all the work. 

That is it!

And of course the script is GPL!

So anyone looking for the script ???

---

### Post by Artiom on 2004-12-29
I just ment that you should try to add features yourself, if you have any problems with it, show us what you did, so we can help.

you always can google for shell scripting  :mrgreen:

---

