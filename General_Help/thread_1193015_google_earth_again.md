---
title: "google earth again"
date: 2009-06-21
forum: General Help
---

### Post by blur xc on 2009-06-21
I know you guys are probably tiring of hearing my belly aching about this subject, but here's what I get when I run google earth.  I list of error messages, and a black screen.

Now, I know I'm not supposed to, but if I run it w/ root powers it works fine.  No errors, globe shows right up...

Thanks,
BM

---

### Post by rushikesh988 on 2009-06-21
I think you should try to create these directories by hand ....



:D

I think  that will help you ....

---

### Post by DeMus on 2009-06-21
> **Barna Madau said:**
> I know you guys are probably tiring of hearing my belly aching about this subject, but here's what I get when I run google earth.  I list of error messages, and a black screen.

Now, I know I'm not supposed to, but if I run it w/ root powers it works fine.  No errors, globe shows right up...

Thanks,
BM

How did you install it? From the repos or directly from the Google site?
When installing it from the Google site, try to install it without using sudo, it will then be installed inside your home folder.
When things should not work afterwards, you can simply delete the folder from your home folder and it is gone again.
There is (or hopefully was) one thing: Googleearth installs one file which is not compatible with your OS. You should delete that file so the program will look for it in the standard folders and thus uses another (the right) version of it.
The file is called: libcrypto.so.0.9.8
Either delete it or use```
 mv libcrypto.so.0.9.8 libcrypto.so.0.9.8_old
```
to rename it

---

### Post by trikster_x on 2009-06-21
I checked out one of your other posts and the problem seems to be some bad info.  I notice d you used this method to install the .bin file:
```
cd Desktop
chmod a+x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin
```

The reason google earth is trying to create root files is because of the addition of that little sudo command.  That told linux to go ahead and install GE as root.  If you remove the sudo command, it will install in whatever directory you tell it to:
```
cd Desktop
chmod a+x GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

Doing it this way let's linux know you want to run it on a user level only.  If you have multiple users on your machine that want to use the program, you may have to install on each user's account.  

One thing about following install commands to remember is to be suspect ANY time you are told to use the sudo command.  It never hurts to try it without the sudo command first.  The worst that will happen then is you have to uninstall the program.  Running as root, the worst that can happen is a complete system failure.

---

### Post by blur xc on 2009-06-21
I know, I installed it that way first- but I uninstalled it and reinstalled it from the repos...

renaming that libcrypto file didn't' work either...

thanks,
BM

---

### Post by blur xc on 2009-06-22
Well, I screwed around a lot trying to make sense of the vague suggestions popping up in old threads on how to fix this (everyone assumes you know some amount about linux and only post half of the information).

I ended up unistalling it from synaptic and reinstalling from the bin file because most of the help suggestions related to this method of installing it. After fixing the problem, it turns out I probably could have done the same thing to the one from synaptic.  It looks like there's a problem with Google Earth 5.0.

Here's the fix- [http://ubuntuforums.org/archive/index.php/t-1070362.html](http://ubuntuforums.org/archive/index.php/t-1070362.html) from this thread

> "For the "Could not create directory: /root/.googleerth/Cache" problem, edit your .config/Google/GoogleEarthPlus.conf replacing /root with your home directory for the following two lines:

```
KMLPath=/root/.googleearth
CachePath=/root/.googleearth/Cache
```"For those as confused as I was- the .config directory is under your home folder.

```
home/<user_name>/.config/Google/GoogleEarthPlus.conf
```the edited lines should looke like:
```
KMLPath=/home/<user_name>/.googleearth
CachePath=/home/<user_name>/.googleearth/Cache
```Hope it works for you...

BM

---

### Post by rojulian on 2009-06-23
Hi
i have a gps over google earth tracking software made for windows and i switched to ubuntu and i need to make it work
i've installed the program (with wine), called gootrac and google earth (in linux)
gootrac sends information about location to google earth, but it sais that i do not have it installed.
can anyone help me with some info on how to make google earth recognized by gootrac?

---

### Post by blur xc on 2009-06-23
I have no knowledge of gootrac, but can I ask what gps unit you are using?  I always used Garmin's Motion Based website.  I could upload my gps data, and view it on their interface, or download it in a variety of formats, one being .kml files.  Now motion based has been replaced with another service, but I can't remember what it's called...  

I've never used wine, but could you install a windows version of google earth in it, and see if that will let the two programs talk to each other?

BM

---

### Post by rojulian on 2009-06-24
i have installed the GoogleEarth-Win-Plus-5.0.11733.9347 using wine but i get the black screen (i have an acer aspire 5315 with mobile intel graphics media accelerator x3100) -compiz works well.
i have a vechicle tracking kit and the program provided (gootrac) uses google earth
I think it gets the information about the device from gprs using the internet (or something like that) and shows the coordanates in google earth.
I have google earth for linux but the quality is poor (when i rotate the globe it scrambles the image - but i can't use the linux version with my program)

---

### Post by jhb1608 on 2009-11-02
> **blur xc said:**
> Well, I screwed around a lot trying to make sense of the vague suggestions popping up in old threads on how to fix this (everyone assumes you know some amount about linux and only post half of the information).

I ended up unistalling it from synaptic and reinstalling from the bin file because most of the help suggestions related to this method of installing it. After fixing the problem, it turns out I probably could have done the same thing to the one from synaptic.  It looks like there's a problem with Google Earth 5.0.

Here's the fix- [http://ubuntuforums.org/archive/index.php/t-1070362.html](http://ubuntuforums.org/archive/index.php/t-1070362.html) from this thread

For those as confused as I was- the .config directory is under your home folder.

```
home/<user_name>/.conf/Google/GoogleEarthPlus.conf
```the edited lines should looke like:
```
KMLPath=/home/<user_name>/.googleearth
CachePath=/home/<user_name>/.googleearth/Cache
```Hope it works for you...

BM

I followed your tutorial and got this:

Could not find "/home/jason/.conf/Google/GoogleEarthPlus.conf".

Help?

---

### Post by cowboy7305 on 2009-11-02
[http://ubuntuguide.net/how-to-install-google-earth-in-ubuntu-904](http://ubuntuguide.net/how-to-install-google-earth-in-ubuntu-904)
look at this site 
worked for me and its dead easy even i managed it

---

### Post by blur xc on 2009-11-02
> **jhb1608 said:**
> I followed your tutorial and got this:

Could not find "/home/jason/.conf/Google/GoogleEarthPlus.conf".

Help?

Browse around and see if there's a GoogleEarthPlus.conf somewhere else???

BM

---

### Post by dcstar on 2009-11-02
> **blur xc said:**
> Browse around and see if there's a GoogleEarthPlus.conf somewhere else???

BM

/home/jason/**.config**/Google/GoogleEarthPlus.conf

---

### Post by blur xc on 2009-11-03
> **dcstar said:**
> /home/jason/**.config**/Google/GoogleEarthPlus.conf


My bad- fixed original post...

BM

---

