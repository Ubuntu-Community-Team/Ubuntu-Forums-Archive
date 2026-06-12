---
title: "install Wolfenstein:Enemy Territory problem"
date: 2008-01-30
forum: Gaming &amp; Leisure
---

### Post by scottc992004 on 2008-01-30
i get up to choosing where to install it defualt path is " /urs/local/games/ " but it says that i cannot write there so if i change it to any other path it still says the same thing. has anyone come across this problem or knows the correct path?

---

### Post by shiver on 2008-01-30
It fails because you don't have privileges to that directory. You either need to run the install with sudo or install to your home dir.

---

### Post by combatghoul on 2008-01-30
From past experience,

i find that with regards to the updates and the maps needed for the different servers for ET, just connect to the server and all the maps and updates will be downloaded automagically for you.


Its best to just install the base 2.60 ET program, not forgetting the chmod step mentioned in the other posts.

An additional step i did was also to link the ET launcher to my desktop so i didnt have to goto terminal each time to run it.

i usually have to disable moblock-nfq as well if its installed as I find it interferes with ET.

sudo /etc/init.d/moblock-nfq stop

Portforwarding on yr router should also be set to the appropriate port.

hope this helps a little.

---

### Post by scottc992004 on 2008-01-31
ok tried 

chmod +x et-linux-2.60.x86.run
su -c "./et-linux-2.60.x86.run"

and this is what it says:

scott@scott-desktop:~$ chmod +x et-linux-2.60.x86.run
chmod: cannot access `et-linux-2.60.x86.run': No such file or directory
scott@scott-desktop:~$ su -c "./et-linux-2.60.x86.run"
Password: 
su: Authentication failure
Sorry.
scott@scott-desktop:~$ sudo -c "./et-linux-2.60.x86.run"
sudo: illegal option `-c'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
scott@scott-desktop:~$ 


how can i get it to work?  :confused:

---

### Post by frodon on 2008-01-31
All about standard install is here :
[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

---

### Post by scottc992004 on 2008-02-01
where does the file et-linux-2.60.x86.run need to be to change the permissions so that the line "sudo chmod +x et-linux-2.60.x86.run"
can work because i have the file on my desktop and when i use  "sudo chmod +x et-linux-2.60.x86.run" i get:

scott@scott-desktop:~$ sudo chmod +x et-linux-2.60.x86.run
chmod: cannot access `et-linux-2.60.x86.run': No such file or directory
scott@scott-desktop:~$

---

### Post by frodon on 2008-02-01
As i told you in PM just go in you desktop folder first using command line :
```
cd ~/Desptop
sudo chmod +x et-linux-2.60.x86.run
```

Hope it is ok for you now :)

---

### Post by scottc992004 on 2008-02-01
I ran the command line

cd ~/Desktop
sudo chmod +x et-linux-2.60.x86.run

but nothing happens

scott@scott-desktop:~$ cd ~/Desktop
scott@scott-desktop:~/Desktop$ sudo chmod +x et-linux-2.60.x86.run
scott@scott-desktop:~/Desktop$ 

i have taken a screenshot if it would help.

---

### Post by frodon on 2008-02-01
So that means it worked ;)

Go to next step and run the file
```
cd ~/Desktop
sudo sh ./et-linux-2.60.x86.run
```

Then after do the same for the update and finally i would recomend you to apply the 2.60b patch though it is not mandatory.
To apply the 2.6b patch just download it through the following link then extract the files from the archive made for linux in your install directory, it should overwrite some files :
[http://www.liberty-gaming.org/index.php?option=com_remository&Itemid=29&func=download&id=9&chk=79b8745e1c9d6da42a6d24946d56d367&no_html=1](http://www.liberty-gaming.org/index.php?option=com_remository&Itemid=29&func=download&id=9&chk=79b8745e1c9d6da42a6d24946d56d367&no_html=1)

---

### Post by scottc992004 on 2008-02-01
The game is installed. I downloaded the patch but i cant extract it to the enemy territory folder is there a way to do it with the terminal?

and when i started the game i just got a black screen and couldn't hear anything?

---

### Post by scottc992004 on 2008-02-01
It's ok fixed it i ran the command line "sudo apt-get install esound" and i had sound and could see. 

Thank you very much for your help frodon.

:)

---

### Post by frodon on 2008-02-01
We will see for the patch later, for your sound the following commans should solve tyhe issue but please note that no apps using your sound card should be opened when starting ET (e.g. music player) :
```
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit
```If you don't want to type this each time you start your computer you can use Method3 in the link i gave you (post #5)

For the black screen, first check that you have installed your graphic driver then type the following command :
```
glxinfo | grep render
```If it answer "direct rendering: No " then the problem come from your graphic driver.

EDIT: oups just saw you got this fixed, for the patch extract the file to overwrite on your desktop then open the file browser with root rights "gksudo nautilus" then use the opened file browser window to overwrite the files in your ET directory then close the file browser.

Maybe we will meet us on server (link of the ET community i run in my sig)

---

### Post by scottc992004 on 2008-02-01
one more thing every time i start the game i need to create my player profile. how can i keep my profile?

---

### Post by frodon on 2008-02-01
This is not supposed to happen except if you delete your ".etwolf" directory which is located in your home directory.
Check if this directory exist in you home directory (don't forget to enable hidden file viewing as it is an hidden directory).

If you have this directory check if you see inside a file called "etkey", this is your key which will allow servers to identify you, so if you want to re-install ET later without losing your key just save it somewhere and put it back on your new install. When you create your profile don't forget to enable punkbuster.

---

### Post by scottc992004 on 2008-02-01
searched for both files with show hidden files on and cannot find them so i guess i'll just reinstall et.

---

### Post by frodon on 2008-02-01
Hmm, that's strange, if you do "ls -la ~/.etwolf" you see nothing ?

Even if not existing ET should create it automatically, anyway if this directory doesn't exist then just create it and it should be good :
```
mkdir ~/.etwolf
```

---

### Post by scottc992004 on 2008-02-01
how do i uninstall et

---

### Post by scottc992004 on 2008-02-01
using "ls -la ~/.etwolf"

I get:

scott@scott-desktop:~$ ls -la ~/.etwolf
total 16
drwxr-xr-x  4 root  root  4096 2008-02-01 21:42 .
drwxr-xr-x 43 scott scott 4096 2008-02-01 22:50 ..
drwxr-xr-x  2 root  root  4096 2008-02-01 21:42 etmain
drwxr-xr-x  2 root  root  4096 2008-02-01 21:42 pb
scott@scott-desktop:~$

---

### Post by frodon on 2008-02-01
To uninstall ET it is rather simple, just delete your ET install directory as well as your .etwolf directory.
According to the output you get your .etwolf directory is well created so it should just work, maybe try again to create your profile, join a server then exit and open the game again to see if your profile is saved.

---

### Post by scottc992004 on 2008-02-01
everytime i go to join a server it closes the game.

where would the .etwolf directory be located?

---

### Post by frodon on 2008-02-01
What error message do you get ?

The .etwolf directory is located in your home directory.

EDIT: ok i understood, your .etwolf directory has root user as owner whereas it should just be normal user as owner, type the following command to fix this :
```
sudo chown -R *put_your_username_here* ~/.etwolf
```

---

### Post by scottc992004 on 2008-02-01
no error message it just closes after waiting around 1 minute to join a server

---

### Post by frodon on 2008-02-01
I edited my previous post with the fix to your problem, i didn't whatch your log carefully enough the first time i did.

---

### Post by scottc992004 on 2008-02-01
scott@scott-desktop:~$ sudo chown -R scott ~/ .ewolf
[sudo] password for scott:
scott@scott-desktop:~$

does this mean it did it?

---

### Post by frodon on 2008-02-01
yes :)

If you need further help or ET training feel free to ask i would be really pleased to kill you or maybe be killed by you :P

---

### Post by scottc992004 on 2008-02-01
it's working :)

hope we run into eachother on et. 
my username is scottc992004

---

### Post by scottc992004 on 2008-02-01
downloads maps and things. comes up with an error

Server disconnected for unknown reason

The following packs are missing:
etmain/temple_final.pk3
etmain/resurrection.pk3
etmain/etdo_fueldepot.pk3
etmain/cortex_who_6_2.pk3
etmain/axislab_b2.pk3

do i need to update something and how?

---

### Post by frodon on 2008-02-01
It depends of the server setting but in most of cases server will make you automatically download the maps or missing files you need to play on the selected server.

Just in case give me the output of "ls -la ~/.etwolf" again or just check that there's no more directories or files owned by root user.

Try to connect the server hosted by the community i run so i can guaranty you 100% that you should get all the files automatically downloaded. To do that quickly, once in ET open the console pressing "~" character and type "/connect  85.214.123.186:27960"
If you are not able to connect then there's still a rights problem somewhere.

---

### Post by scottc992004 on 2008-02-01
scott@scott-desktop:~$ ls -la ~/.etwolf
total 16
drwxr-xr-x  4 scott scott 4096 2008-02-01 21:42 .
drwxr-xr-x 43 scott scott 4096 2008-02-01 23:07 ..
drwxr-xr-x  3 scott scott 4096 2008-02-02 00:35 etmain
drwxr-xr-x  5 scott scott 4096 2008-02-01 23:37 pb
scott@scott-desktop:~$

---

### Post by frodon on 2008-02-01
Looks good, try on the server i gave you and tell me how it goes.

---

### Post by scottc992004 on 2008-02-01
it was giving me a time of 27 hours and rising so i'll try it later.

but as soon as i try the ip address my friend gave me it closes the game.

---

### Post by frodon on 2008-02-01
Ok so maybe it is a problem especially with the server of your friend.

Good luck ;)

---

### Post by scottc992004 on 2008-02-13
it still comes up with,

server disconnected for unknown reason

The following packs are missing:
etmain/temple_final.pk3
etmain/resurrection.pk3
etmain/etdo_fueldepot.pk3
etmain/cortex_who_6_2.pk3
etmain/axislab_b2.pk3

on any server just different files.

---

### Post by frodon on 2008-02-13
Something should be preventing you from downloading the missing packs automatically, check if there's an option in game to prevent this.

Did you try on other servers ?

---

### Post by scottc992004 on 2008-02-14
yes i tried the server you told me, my friends server and one out of the list.i'll check if i can change any settings but from what i can remember i don't think there is a setting for that.

---

### Post by scottc992004 on 2008-02-16
no i can not find any option in the game that could be skipping those files.

---

### Post by articpenguin on 2008-02-17
why does my router hang everytime i trie to connect?

---

### Post by frodon on 2008-02-19
> **scottc992004 said:**
> no i can not find any option in the game that could be skipping those files.Then you can try something brutal, delete or rename to something else your .etwolf folder so that ET will create it again, in some cases it has been reported to be the only working solution.
You will lose your ET settings doing that.

---

