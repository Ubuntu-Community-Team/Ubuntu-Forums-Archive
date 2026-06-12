---
title: "installing realplayer"
date: 2005-10-19
forum: Desktop Environments
---

### Post by sjpritch25 on 2005-10-19
Having problems with realplayer install
> sudo apt-get install realplayer
Is the command i am using.  I go through the install, however, the file i downloaded from real's website is not the correct .rpm file.  I didn't write down what the file should be.  But, here is the file i downloaded
> RealPlayer10GOLD.rpm
Where can i download the correct file???:confused: 
Any help would be great!!!!!!!!!

---

### Post by adwait on 2005-10-19
The file on the site and apt-get are unrelated. apt-get downloads and installs software from the repositories. On the other hand, if you want to install the file you downloaded, you can convert it to an deb file using alien:
```
alien RealPlayer10GOLD.rpm
```

After that, it will create a deb file which you can install using
```
dpkg -i <filename_of_deb>
```

I believe there is bin file available as well, with which you can compile on your own...I suggest you do that because alien does not always work.

---

### Post by sjpritch25 on 2005-10-20
i downloaded the .bin file, but  i am a newbie.  I am learning, however, i don't know the commands to compile the .bin file.  Could you please show me???:confused:

---

### Post by manicka on 2005-10-20
I use the alien method to make a realplayer deb file. It installs and runs without problems.
I agree that alien is not a very desirbale method but in this case it works just fine.

---

### Post by sso71 on 2005-10-20
I download RealPlayer10GOLD.bin and following the instruction from real.com and I also install build-essential from apt-get. However, ./RealPlayer10GOLD.bin needs libstdc++.so.5, but my system only has libstdc++.so.6. What should I do from here? 
I will try the conversion method, but I still want to learn how to "down-grade" the libstdc++. Thanks!:confused:

---

### Post by RAOF on 2005-10-20
You can just install libstdc++5.  It will install alongside libstdc++6.  It's really easy:
1)Open synaptic.
2)Click "search" - search for "libstdc++"
3)You should be able to find a "libstdc++5" and "libstdc++6".  Version 6 should be installed (have a green box next to it), and version 5 not installed.  Select libstdc++5 to install.
4)Click "apply".  Synaptic will now work its magic, downloading the new library, installing it, and setting it up.

Learn to love synaptic.  The search a really useful way to solve these sort of (dependency) problems :)

---

### Post by sso71 on 2005-10-20
Got it to work, thanks a lot!

---

### Post by sjpritch25 on 2005-10-20
[QUOTE=adwait]The file on the site and apt-get are unrelated. apt-get downloads and installs software from the repositories. On the other hand, if you want to install the file you downloaded, you can convert it to an deb file using alien:
```
alien RealPlayer10GOLD.rpm
```

After that, it will create a deb file which you can install using
```
dpkg -i <filename_of_deb>
```

I believe there is bin file available as well, with which you can compile on your own...I suggest you do that because alien does not always work.[/QUOTE]

Thanks for the reply
I just need some help with the command.  My RealPlayer10GOLD.rpm file is in my **/home** directory.  I am having some trouble running the alien command.  I need some assistance is using the terminal to get to the RealPlayer file.  I have only been using linux for a couple of weeks and i am just learning to get familier with the terminal commands. Thanks for all your help.

---

### Post by manicka on 2005-10-20
try

```
sudo alien RealPlayer10GOLD.rpm
sudo dpkg -i <filename_of_deb>
```

---

### Post by ALai on 2005-10-21
I have problem setting up RealPlayer too. 
I followed your tips and download RealPlayer10GOLD.bin 
and libstdc++.so.5. I successfully unpacked the file (Thanks for your tips)
but now I can't still get it running in Firefox. 

Do  I need to set up something else in Firefox?

Thanks,

AL

---

### Post by Riverside on 2005-10-21
[QUOTE=ALai]I have problem setting up RealPlayer too. 
I followed your tips and download RealPlayer10GOLD.bin 
and libstdc++.so.5. I successfully unpacked the file (Thanks for your tips)
but now I can't still get it running in Firefox. 

Do  I need to set up something else in Firefox?[/QUOTE]Log out of your current X session, and then log back in.  You should then find that the Firefox Real Player plugin will work.

---

### Post by james4e on 2005-10-21
[QUOTE=manicka]try

```
sudo alien RealPlayer10GOLD.rpm
sudo dpkg -i <filename_of_deb>
```[/QUOTE]

You can also use the following command to install the .rpm file.
```

sudo alien -i Realplayer10GOLD.rpm

```

---

### Post by subscrive on 2005-10-31
the easy way is as follows:

search for helix player on google and go to their official website.

from the download section choose either the binary of helix player or real player.
choose binary!

now change the permission of the downloaded file and then run the script.

enjoy!

~A.

---

### Post by matthewv on 2005-10-31
I found the easiest way to install real player is to follow the instructions in the ubuntu starter guide, found by pressing the life ring on the top panel. Here's what they say:
> 


How do I install RealPlayer 10?

       1.

          Visit [http://www.real.com/linux/](http://www.real.com/linux/) and download Realplayer 10 for Linux into a convenient directory.
       2.

          Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type

chmod +x RealPlayer10GOLD.bin

       3.

          To install Real Player 10, run the downloaded file. Type

sudo ./RealPlayer10GOLD.bin

          When prompted for a location to install RealPlayer 10, type /usr/bin/RealPlayer

          When prompted to configure system-wide symbolic links, type "y". After that, accept the default prefix for symbolic links.
       4.

          You can now safely remove the downloaded file from your system. Type

rm RealPlayer10GOLD.bin

       5.

          To run Real Player 10, choose Applications &#8594; Sound & Applications &#8594; RealPlayer 10.



---

