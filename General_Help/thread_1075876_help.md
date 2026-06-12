---
title: "help"
date: 2009-02-20
forum: General Help
---

### Post by gib23 on 2009-02-20
how do i go to terminal and access cdrom then access a setup.exe file in terminal?

---

### Post by N4zgu1 on 2009-02-20
You cannot, linux cannot open .exe files, maybe you can try with wine, but it doesnt always work.


What are you trying to execute??

---

### Post by gib23 on 2009-02-20
i am trying to follow the wine instructions for installing gta vc it comes with this error message

wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found

how can i fix this

---

### Post by neu2buntu on 2009-02-20
where is your .exe file at do you have it on cd? or where?

---

### Post by gib23 on 2009-02-20
yes its on a cd

---

### Post by howefield on 2009-02-20
Is it GTA - Vice City ?

Here is a walk through of the procedure

[http://www.ubuntu-unleashed.com/2008/05/did-you-know-grand-theft-auto-vice-city.html](http://www.ubuntu-unleashed.com/2008/05/did-you-know-grand-theft-auto-vice-city.html)

---

### Post by donkyhotay on 2009-02-20
Depends on your configuration and the name of the GTA installer, this may not be exact but in the terminal try something along the lines of
```
cd /media/cdrom
wine ./setup.exe
```
cd is the command to change your directory, ls is the command to view while files are in the directory. All removable drives are located in the folder /media but your may be cdrom1 or something similar (I don't know). You might need to cd into each directory and use ls for listing to know where to go next.

---

### Post by neu2buntu on 2009-02-20
there should be no need to go through the terminal to run an .exe of cd as far as i know, right well if you have wine installed you should be able to go into your cdrom folder(this should automount) and right click on the .grand theft file and choose "open with wine program loader"    are you sure this isnt an .iso image of the game that has to be mounted?

---

### Post by gib23 on 2009-02-20
it now says that there is an error: Not ready

---

### Post by neu2buntu on 2009-02-20
read through the setup for your game now.  have you copied the .exe patch to the .wine drive c so far?

---

### Post by gib23 on 2009-02-20
how do i run it now where is it located i can not locate it 


thanks for the installation help

---

### Post by neu2buntu on 2009-02-20
if you have followed step by step as in howefields post ,then you should be able to goto the top menu >Applications > wine > programs > and it should be in the list there.... is this the exact method you have done to install "gta" it is quite complicated if you r a total noob?

---

### Post by gib23 on 2009-02-20
yes i am a total noob i just got xubuntu iso files 
First I grabbed the vice city isos and moved them to /home/$USER/GTA
So I then wanted to mount the iso's and install, I simply grabbed fuseiso and wine then added myself to the fuse group so I can mount iso's:
sudo apt-get install fuseiso wine ; sudo adduser $USER fuseiso


how do i do this

---

### Post by neu2buntu on 2009-02-20
this part ...$USER ...has to be your username in these commands.. so say for example your name is dave the command would be /home/dave/GTA ...you get the idea?
maybe you know some of this stuff ,but i will treat it like you dont...lol
    isnt xubuntu all command line (terminal)? i would have struggled when i first switched from windows.    let me know exactly what you have done so far as in where the 2 .iso files are ...every bit of info is needed for your help... hopefully you have just been typing USER ...lol

---

### Post by gib23 on 2009-02-20
i don't know what the iso files are i did follow the wine commands i found on the internet and it installed i found it but it wount run because of a lack of video memory i have nothing installed on this computer

---

### Post by neu2buntu on 2009-02-20
the .iso files are images (exact copies) of the 2 cds that you would get for the game .so if they are both mounted together you will need at least 1.4gb of memory (ram) to run it, so say if your computer is only 1gb of ram this will not work. what are your specs? how much ram?

---

### Post by neu2buntu on 2009-02-20
maybe im not exact in saying it wont work, the swap partition may hold some of the memory needed, and possibly the .iso images are not full. check the properties of the 2 iso files to see the total size (mb). when i mount any iso,s in ubuntu i use Gmount-iso and mount the iso in /media/FILE_I_HAVE_CREATED , and add the directory to wine config.  also making a symbolic link to the directory where the iso is mounted as wine seems to have problems seeing it.

---

### Post by neu2buntu on 2009-02-21
gib23 have you had a look at your bios settings for video ram (usually Ecs ,f2 or f12 as you are booting) and see if you can increase the amount of video ram there. i have looked around for you and some posts have said you can also edit these settings in the /etx/X11/xorg.conf file but i cannot see any settings for video ram on my acer-aspire-one but your computer may be different. another thing(my own idea) would be maybe just mount 1 .iso (cd image) at a time until you are prompted to insert(mount) the other one.

 i have had a problem similar to yours where i try to run my installation of backtrack3 but have lack of video ram(8mb) on the acer but it will run when i use the same backtrack from a usb installation,so the laptop is capable of running it. as far as i rememder the video ram expands when required....
 


also try burning the 2 iso files to 2 seperate cds and just run them from your cd/dvd rom drive instead of mounting them as images to see how it goes...

---

