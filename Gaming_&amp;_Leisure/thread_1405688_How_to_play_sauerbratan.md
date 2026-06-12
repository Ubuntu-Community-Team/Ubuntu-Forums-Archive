---
title: "How to play sauerbratan?"
date: 2010-02-12
forum: Gaming &amp; Leisure
---

### Post by Evilhugbear on 2010-02-12
Hello, I just download the game sauerbraten. I put the folder in my home directory. I then go into that folder, and double click sauerbraten unix. I don't know what to do after that. I click run and run in terminal.

Am I doing something wrong? Is everything wrong?

I have 64 bit ubuntu 9.10

---

### Post by tommcd on 2010-02-13
The terminal is your friend. So open a terminal. 
When the terminal opens, cd (change directory) to the sauerbraten directory in your home directory:
```
cd ~/sauer
``` 
and hit the TAB key. It should autocomplete the name of the sauerbraten directory, then hit enter. Alternatively you can type the full name of the sauerbraten directory. (Remember linux is case sensitive here).
Then make sure the sauerbraten_unix file is executable:
```
ls -l
```
It should report these permissions for sauerbraten_unix:
```
-rwxr-xr-x  1 tom users    1599 2009-02-14 13:51 sauerbraten_unix

```
The "x" in the permissions means that it is executable.
If it is not executable, then make it so:
```
chmod +x sauerbraten_unix
```
Then to run it:
```
./sauerbraten_unix
```
This should work for both 32bit and 64bit Ubuntu.
This is covered in the Sauerbraten wiki:
[http://cube.wikispaces.com/Install+Guide](http://cube.wikispaces.com/Install+Guide)
Note: If you run ./sauerbraten_unix and get an error about some missing library, then write back. If I remember correctly, I had to install some dependency in Ubuntu to get it to work. The game runs fine as it is on Slackware.

---

### Post by Perfect Storm on 2010-02-13
As I recalled it the binary is 32-bit (if they haven't changed it since the last time I tried it). Though you can compile it to build 64-bit binary.

I have an old guide (back in 7.10): [http://gwos.org/doku.php/guides:64bit:sauerbraten](http://gwos.org/doku.php/guides:64bit:sauerbraten)

---

### Post by Evilhugbear on 2010-02-13
> **tommcd said:**
> The terminal is your friend. So open a terminal. 
When the terminal opens, cd (change directory) to the sauerbraten directory in your home directory:
```
cd ~/sauer
```and hit the TAB key. It should autocomplete the name of the sauerbraten directory, then hit enter. Alternatively you can type the full name of the sauerbraten directory. (Remember linux is case sensitive here).
Then make sure the sauerbraten_unix file is executable:
```
ls -l
```It should report these permissions for sauerbraten_unix:
```
-rwxr-xr-x  1 tom users    1599 2009-02-14 13:51 sauerbraten_unix

```The "x" in the permissions means that it is executable.
If it is not executable, then make it so:
```
chmod +x sauerbraten_unix
```Then to run it:
```
./sauerbraten_unix
```This should work for both 32bit and 64bit Ubuntu.
This is covered in the Sauerbraten wiki:
[http://cube.wikispaces.com/Install+Guide](http://cube.wikispaces.com/Install+Guide)
Note: If you run ./sauerbraten_unix and get an error about some missing library, then write back. If I remember correctly, I had to install some dependency in Ubuntu to get it to work. The game runs fine as it is on Slackware.

When I do ls -l it says total 0. What does that mean?

---

### Post by Evilhugbear on 2010-02-13
> **Artificial Intelligence said:**
> As I recalled it the binary is 32-bit (if they haven't changed it since the last time I tried it). Though you can compile it to build 64-bit binary.

I have an old guide (back in 7.10): [http://gwos.org/doku.php/guides:64bit:sauerbraten](http://gwos.org/doku.php/guides:64bit:sauerbraten)

I followed your guide, and when I click sauerbraten in the menu nothing happens :confused:

---

### Post by Perfect Storm on 2010-02-13
> **Evilhugbear said:**
> I followed your guide, and when I click sauerbraten in the menu nothing happens :confused:

It's a bit old guide, so there might be some adjustment that need to be done for the guide.

Anyway, 
```
sh -c "cd ~/.Games/sauerbraten && ./sauerbraten_unix"
```
What's the output?

---

### Post by Butthead on 2010-02-13
Isn't Sauerbraten in the repros?  I have it listed in the "games" section in ancient Hardy 8.04. :confused:

---

### Post by Perfect Storm on 2010-02-14
> **Butthead said:**
> Isn't Sauerbraten in the repros?  I have it listed in the "games" section in ancient Hardy 8.04. :confused:

Aye, but he most have his reason?

```
sudo apt-get install sauerbraten
```

---

### Post by tommcd on 2010-02-14
> **Evilhugbear said:**
> When I do ls -l it says total 0. What does that mean?
First, lets start from square 1.
Download the linux sauerbraten .tar.bz file from here:
[http://cubeengine.com/files.php4](http://cubeengine.com/files.php4)
If you still have that file in your home directory then you can omit this.
Then untar it:
```
tar -xvjf sauerbraten_2009_05_04_trooper_edition_linux.tar.bz2
```
Again, you can just type **tar -xvjf sauer** and hit the TAB key and it should autocomplete the name of the sauerbraten .tar.bz file.
Then cd into the sauerbraten directory that was created when you untarred the .tar.bz file:
```
cd sauerbraten/
```
Verify that you are indeed in the sauerbraten directory:
```
pwd
```
The pwd command = print working directory. It should report:
```
~/sauerbraten
```
or something like that. Then **ls -l** should report the contents and the permissions of everything in the sauerbraten directory.
The ./sauerbraten_uninx command works in 64bit Slackware. I am running 32bit Ubuntu, so I can't test it in 64bit Ubuntu.

FYI, When you run ./sauerbraten_unix you may get an error that says it can't find  libsdl-image1.2, or something like that. The solution is to install  libsdl-image1.2.
```
sudo apt-get install  libsdl-image1.2
```
Then ./sauerbraten_unix will work.

---

