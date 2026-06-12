---
title: "americas army"
date: 2007-04-28
forum: Gaming &amp; Leisure
---

### Post by stonecold23 on 2007-04-28
have downloaded the linux file
there are now two files on the desktop
they are called:
armyops250linux.run.part
and
X6.htm
what do i do with them to install Americas army
 
when i click on them i get this error message:
could not open the file home/phil/desktop/armyops250linux.run.part
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

is there any automatic installation files out there to do all this for me?

---

### Post by Najand on 2007-04-28
It has not downloaded completely yet

---

### Post by stonecold23 on 2007-04-28
but it told me it had finished downloading an hour ago?

---

### Post by Najand on 2007-04-28
Wel, the file does not seems to be finished yet... Write click on it and check its size and compare it with the original file...  I believe you cannot download such file in an hour or two... It is too huge and it takes time to get downloaded.

---

### Post by stonecold23 on 2007-04-28
have restarted download and deleted old files.
should be about 10 mins time. bt 8mb is downloading at 900kb/s!
only ever got 600 at highest with windows ... maybe its irelevant.

how do i go about installing a binary file then?

---

### Post by Najand on 2007-04-28
When finished run it in the terminal:
$ cd DIRECTORY
$ ./FILENAME

---

### Post by stonecold23 on 2007-04-28
how do i know what the cd directory is? since there isnt a cd? i'm confused

heres what i just did:
phil@Phil-Desktop:~$ cd /home/phil/Desktop
phil@Phil-Desktop:~/Desktop$ armyops250linux.run
bash: armyops250linux.run: command not found
phil@Phil-Desktop:~/Desktop$

---

### Post by predaeus on 2007-04-28
you can read up on shell commands in tutorials like this [http://www.linuxcommand.org/lts0020.php](http://www.linuxcommand.org/lts0020.php)

---

### Post by Vixis on 2007-04-28
If you download file to desktop, copy to the terminal (note you may need to use sudo at second part):
cd ~/Desktop/
./armyops250linux.run

---

### Post by bulldog on 2007-04-28
cd means 'change directory':) 
You have to go into the place where  the downloaded file is located.
If it's on your desktop,you have to type in your terminal 'cd Desktop' to get there.
Keep in mind Linux makes  a difference between upper- and lower case caracters!

---

### Post by stonecold23 on 2007-04-28
phil@Phil-Desktop:~/Desktop$ cd /home/phil/Desktop
phil@Phil-Desktop:~/Desktop$ ./armyops250linux.run
bash: ./armyops250linux.run: Permission denied
phil@Phil-Desktop:~/Desktop$ 

error why no permission. of i put sudo in front of it should it ask for password?

---

### Post by predaeus on 2007-04-28
> **stonecold23 said:**
> how do i know what the cd directory is? since there isnt a cd? 
phil@Phil-Desktop:~/Desktop$ armyops250linux.run
bash: armyops250linux.run: command not found
phil@Phil-Desktop:~/Desktop$

you need to add the "./" infront like ```
./armyops250linux.run
``` because "." denotes the current directory and shell searches for executables in the global PATH variable.
Probably you need to do  ```
chmod u+x ./armyops250linux.run
```  and then run it. Or just run it like ```
sh armyops250linux.run
```

---

### Post by stonecold23 on 2007-04-28
if you look at the post just above i had already found that mistake but thanks anyway. still didn't find the file. even though i copy and pasted the file name!
ooooo i think its alive at last!
thanks for all the great help peeps! 
now the installer is telling me it doesnt have permission to write to:
/usr/local/games/armyops

---

### Post by stonecold23 on 2007-04-28
i have gone into this directory to try and change the permissions.
under preferences
but it says "you are not the owner so you cannot change these permissions."

---

### Post by Iarwain ben-adar on 2007-04-28
Try to install the game with this
```
sudo ./armyops250linux.run
```


Iarwain

---

### Post by stonecold23 on 2007-04-28
yay it works!.  thank you so much to everyone. who has helped! greatly appreciated!

unlucky for me that the AmericasArmy login server is down. apparently maintenance :( 

again thanks u lot rook! :guitar:

---

### Post by kinematic on 2007-04-28
> **Najand said:**
> I believe you cannot download such file in an hour or two... It is too huge and it takes time to get downloaded.

sure you can depending on the speed of your connection.....i d'loaded the feisty fawn cd in 20 minutes ;)

---

### Post by Najand on 2007-04-28
I downloaded it in 3 minute (We have an ubuntu mirror in our network) but not the America Army CD. It is times bigger than ubuntu and usually they are really slow.

---

### Post by stonecold23 on 2007-04-28
yea my download speed was a constant 900kb/s even though we only bought 8mb bt bever get those speeds in xp dont think it has ever reached 700kb/s

how do i actually gain permissions to install the file
do i need to log on as root?
if so how is that done??????????????//

---

### Post by Iarwain ben-adar on 2007-04-28
Look at my previous post :?


Iarwain

---

### Post by stonecold23 on 2007-04-28
phil@Phil-Desktop:~$ cd Desktop
phil@Phil-Desktop:~/Desktop$ sudo ./armyops250linux.run
Password:
sudo: ./armyops250linux.run: command not found

i just tried it and get that error message did i do something wrong?

---

### Post by Iarwain ben-adar on 2007-04-28
Try "sudo ./whatever_the_file_is_called".

That should do the trick (otherwise just login as root to install :?)

```
su
```


Iarwain

---

### Post by K.Mandla on 2007-04-28
(Shifting to Gaming and Leisure. ;) )

---

### Post by stonecold23 on 2007-04-29
sudo ^^^^^^ didn't work keeps telling me file doesnt exist

phil@Phil-Desktop:~$ su
Password: 
su: Authentication failure
Sorry.
phil@Phil-Desktop:~$ 

my password was correct i'm sure why do i not have access?

---

### Post by Ripfox on 2007-04-29
Go to system/administration/users and groups and click on root then properties then reset your root password I think. I hope. lol

---

### Post by WilliamKB on 2007-04-30
I just installed the game last week - here are my steps.

1. Downloaded the '.run' file to my HOME directory because it is easiest to get too.
2. Opened a terminal (it defaults to your home directory).
3. Typed in the terminal 'chmod 755 armyops250linux.run'. If it won't let you do 'chmod' then do 'sudo chmod' and type in your password.
4. Type in the terminal 'gksudo ./armyops250linux.run'. You might need to type your password again.

My self and 1 of my friends did it exactly this way and it worked!

If it still doesn't work I suggest you do 'ls -l' and post the results here so we can verify that you have the correct location, permission and file.

---

### Post by Ripfox on 2007-05-01
Can't you just right click on the file, select properties, select permissions, and tick the box to "allow executing file as a program"

---

### Post by Iarwain ben-adar on 2007-05-02
You can also 'chmod +x armyops250linux.run' ;)


Iarwain

---

### Post by Ripfox on 2007-05-02
Yes but then would he not have to cd to the directory the file was in first? :popcorn:

---

### Post by Iarwain ben-adar on 2007-05-02
lol :D

It all comes down to the same thing, so no worries =)


Iarwain

---

### Post by blitzer on 2007-05-02
This might help:
[https://help.ubuntu.com/community/AmericasArmy]("https://help.ubuntu.com/community/AmericasArmy")

---

### Post by Ripfox on 2007-05-02
Nooo! my way is better!! lol:mad:

---

### Post by Iarwain ben-adar on 2007-05-02
Oh
My
God
;o

Are you ready to start a .... FLAMEWAR ?!?

J/k =)


Iarwain

---

### Post by Ripfox on 2007-05-05
Sounds better than arguing with my gf...lol

---

### Post by brasilforce on 2007-06-11
-

---

### Post by hikaricore on 2007-06-11
> **brasilforce said:**
> I have downloaded the linux file americasarmy-lnxded-281.tar.bz2 
size 2.1gb and i last ununtu disto 7.04


i extract the tar.bz2 and the only file executable i have is a Server.bin at americas army System folder

what do i have  do for install Americas army .2.81 in linux
(Not the w32 version whit wine)

Im very noob in linux but i test to many distro and ubunto for me the best one,

Any help will be aperciated thank you all

Release for the linux client was stopped at version 2.6 I believe.

Although as you have proved the server for AA still exists with linux support.  lol

Follow the guide posted about 5 post prior to yours:

[https://help.ubuntu.com/community/AmericasArmy](https://help.ubuntu.com/community/AmericasArmy)

If you want to install the 2.6 version.

---

### Post by Drakkor on 2007-06-17
I just got AA installed and it runs the first basic training marksmanship weapons training, after that it's all
"unavailable" , probably because it said my internet connection, or server maitenance ??? 
I know my internets up cause I'm posting here, seems to be a bug ?? :confused:

---

### Post by buzzmandt on 2007-06-19
> **Drakkor said:**
> I just got AA installed and it runs the first basic training marksmanship weapons training, after that it's all
"unavailable" , probably because it said my internet connection, or server maitenance ??? 
I know my internets up cause I'm posting here, seems to be a bug ?? :confused:
make sure you do all the basic training, there's 4 i think. then you should be able to play more.  I had to get 38 outta 40 to get expert on the firing range, that unlocked the advanced marksmanship training etc....

---

### Post by tbird64 on 2007-07-29
I have been having problems installing americas army 2.5.

this is what i get from the terminal 


carl@carl-desktop:~/Desktop$ sh ./armyops250-linux.run 
Verifying archive integrity... All good.
Uncompressing America's Army for GNU/Linux 2.5.0.....
Second stage unpacker running...
Starting actual installer...


then it goes back to the prompt and nothing happens.

does anyone know what is going on?

i have ubuntu edgy running on a ppc.

---

### Post by pcjunkie on 2008-04-13
I have managed to install 2.5 (wow memories) but it wont connest to the lan for some reason. Cannot log in...did I miss something?

I chmod to x then used sudo armyops2.5-linux.run to install it. it worked fine. it started fine and runs great but can't log in.

I am also getting this warning
WARNING: ALC_EXT_capture is subject to change!

---

