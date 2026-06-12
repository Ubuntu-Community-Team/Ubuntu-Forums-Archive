---
title: "Installing Real Player 10"
date: 2006-03-04
forum: Desktop Environments
---

### Post by JoeS on 2006-03-04
I downloaded Real Player 10 from [www.real.com/linux](www.real.com/linux).

I then followed the installation instructions:
> - Ensure that the .bin file you downloaded is executable. You can make
  the .bin file executable by running the "chmod a+x
  RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the
    prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up
      assistant will take you through configuring your player.

When I tried to run the .bin file I received the following message:
> Joe@ubuntu:~/Desktop$ ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries:
libstdc++.so.5: cannot open shared object file: No such file or
directory

Can anyone help me to install this?
Thanks.

---

### Post by bluevoodoo1 on 2006-03-04
Try the libstdc++5 package

sudo apt-get install libstdc++5

---

### Post by JoeS on 2006-03-04
Thanks that helped.

I have a further question.
In Ubuntu Help it states:
> When prompted for a location to install RealPlayer 10, type
/usr/bin/RealPlayer

If RealPlayer is installed in the Root directory is it safe to update
from the internet?

---

### Post by Xian on 2006-03-04
[QUOTE=JoeS]If RealPlayer is installed in the Root directory is it safe to update from the internet?[/QUOTE]

I assume you mean the player itself. Many programs on your system place their executables in that directory, but it is (mostly) safe since even during an update you will still have to give write permissions in order for any changes to take place.

---

### Post by JoeS on 2006-03-04
[QUOTE=Xian]I assume you mean the player itself. Many programs on your system place their executables in that directory, but it is (mostly) safe since even during an update you will still have to give write permissions in order for any changes to take place.[/QUOTE]
These are the permissions:
-rwxr-xr-x  1 joe joe 5789348 2006-03-02 20:54 Desktop/RealPlayer10GOLD.bin
I am the owner
Should this be changed?

---

### Post by Xian on 2006-03-04
[QUOTE=JoeS]These are the permissions:
-rwxr-xr-x  1 joe joe 5789348 2006-03-02 20:54 Desktop/RealPlayer10GOLD.bin
I am the owner
Should this be changed?[/QUOTE]

That's just the install bin file. It can be deleted now.

---

### Post by erik-the-red on 2006-03-04
Tell me if you can get Realplayer 10 to run.

It runs for me but when I try to open a file it crashes.

---

### Post by JoeS on 2006-03-06
I can get RealPlayer to run when I open a file. I don't know if this applies to you, but in the Readme file I found this under** known Issues:** 
 > * The value of the UDPPort preference,
       if used, needs to be set as a range,
       for example:

        UseUDPPort=1
        UDPPort=7000-7010

       Setting it to a single number
       will result in a player crash.


---

### Post by 3kravinarayan on 2006-12-03
WHEN I TRY TO ENETR FROM TERMINAL  

it asks for my password but when i type the password it takes no input  why does the password input not take any keys from the keyboard  pl help

Ravi          most of my ubuntu has new been setup  i just need to install real plyer and also looking for rstp to hear BBC   [-(

---

