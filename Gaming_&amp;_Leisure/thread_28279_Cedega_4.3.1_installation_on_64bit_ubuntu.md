---
title: "Cedega 4.3.1 installation on 64bit ubuntu?"
date: 2005-04-19
forum: Gaming &amp; Leisure
---

### Post by janesy on 2005-04-19
Hi,

First post in all, 

Ive just started with linux and ubuntu 64 and learning fast (i hope)

only thing keeping me running windows xppro is gaming, dont do it often but i was CS. So i payed for cedega, point to play via transgaming etc....

Now i find out it doesnt work on 64bit ubuntu. Well as i have been browsing these forums for a while i found a link which showed promise!

[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#UPDATED_AMD64_pure64_w.2F32bit_libs_and_NO_32bit_chroot](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#UPDATED_AMD64_pure64_w.2F32bit_libs_and_NO_32bit_chroot) 

Any way, ive installed it as shown, forcing the deb file to ignor the arch.

(sorry about this)
:  
"
It is now possible on Ubuntu Hoary AMD64 to use Cedega/Point2Play without going through the hassle of building a 32bit chroot. Here are the steps I found worked well for me:

    * Make sure libpng3 is all good 

sudo apt-get install ia32-libs-gtk
sudo apt-get install libpng3
sudo ln -s /usr/lib32/libpng12.so.0.1.2.5 /usr/lib32/libpng.so.3

    * Install cedega and transgaming packages 

sudo dpkg --force-architecture -i transgaming*
sudo dpkg --force-architecture --force-depends -i cedega* ---------------- done this! :)
sudo dpkg --force-architecture -i point2play-small*

    * Edit /usr/bin/cedega to find lib32 --------------- Got here, what eh? :/ in the /usr/bin  there is a file, called cedega, do i have to edit that? cant find where to put that line?

Add: /lib32:/usr/lib32 to the $LD_LIBRARY_PATH ------------------- same as above ^^

    * For Point2Play edit ~/.point2play/.wine_ver/winex-xxx/bin/winex 

Add: /lib32:/usr/lib32 to the $LD_LIBRARY_PATH

I tested with World of Warcraft, Half Life 2/Steam and a few other win32 games I had on my hard drive, everything appears to be working great."


Right i know you will be able to help, as sooo many of you have done before!


thank you

Dave

---

### Post by Muchacho_Gasolino on 2005-04-19
a couple things:
4.3.1 includes libpng3 so that part is not necessary, can't hurt though
you should use point2play, easier to install and configure IMHO

i've done this before, the instructions are a little unclear about some parts
if you are using cedega without point2play, all you should have to do is edit your /usr/bin/cedega file and add in /lib32:/usr/lib32 inside the quotation marks after every time the file says LD_LIBRARY_PATH
at least thats what i did with my point2play file and it worked fine

EDIT: i just looking in my point2play file and it didnt have anything in there about lib32  :-? 
what i first put in there has now been erased somehow
it had been working fine, maybe that isnt necessary anymore

what have your problems with cedega been?

---

### Post by janesy on 2005-04-20
Cedega does not work in 64bit.

only works in native i386, so i had to force it to install on the 64bit arch. (following those directions)

So the file i have to edit is the cedega file in that directory? looks a bit "if" this "if" that tbh.

i will have a look tonight after work.

has any one got cedega and CS working using the 64bit kernal?

thanks

dave


PS. Or how do i install a 32bit ubuntu from scratch? instead of 64.

---

### Post by janesy on 2005-04-20
delete post please, ive decided to just run the i386 on my system, just hope there no performance issues.

thanks for your help.

---

### Post by arbearce on 2005-04-20
I got Cedega to run on my amd64 laptop with a Kubuntu 64bit install here is what I did using the wiki instuction with my comments included.

It is now possible on Ubuntu Hoary AMD64 to use Cedega/Point2Play without going through the hassle of building a 32bit chroot. Here are the steps I found worked well for me:

    * Make sure libpng3 is all good 

sudo apt-get install ia32-libs-gtk
sudo apt-get install libpng3
sudo ln -s /usr/lib32/libpng12.so.0.1.2.5 /usr/lib32/libpng.so.3

    * Install cedega and transgaming packages 

sudo dpkg --force-architecture -i transgaming*
sudo dpkg --force-architecture --force-depends -i cedega*
sudo dpkg --force-architecture -i point2play-small*

    * Edit /usr/bin/cedega to find lib32 

Add: /lib32:/usr/lib32 to the $LD_LIBRARY_PATH

/my comments
Here I opened up a terminal and sudo nano /usr/bin/cedega
Found this line
# Setup LD_LIBRARY_PATH
export LD_LIBRARY_PATH="$WINEXINSTALLDIR/winex/lib:$WINEXINSTALLDIR/winex/bin:$LD_LIBRARY_PATH"
and then tacked on to the end of it /lib32:/usr/lib32 so it looked like this in the end

# Setup LD_LIBRARY_PATH
export LD_LIBRARY_PATH="$WINEXINSTALLDIR/winex/lib:$WINEXINSTALLDIR/winex/bin:$LD_LIBRARY_PATH/lib32:/usr/lib32"

/my comments

    * For Point2Play edit ~/.point2play/.wine_ver/winex-xxx/bin/winex 

Add: /lib32:/usr/lib32 to the $LD_LIBRARY_PATH

/my comments

For this to work first everything had to be installed and I had to run point2play
I tried finding this file this guy was talking about but it wasn't there then after I ran the program it was
so after this dir and file were generated I again, in the terminal window, did a 
sudo nano ~/.point2play/.wine_ver/winex-4.3.1/bin/winex
then I looked for the line that looked like this

# Setup LD_LIBRARY_PATH
export LD_LIBRARY_PATH="$WINEXINSTALLDIR/winex/lib:$WINEXINSTALLDIR/winex/bin:$LD_LIBRARY_PATH/"
and added the lib32:/usr/lib32 to the end of it so it looked like this in the end

# Setup LD_LIBRARY_PATH
export LD_LIBRARY_PATH="$WINEXINSTALLDIR/winex/lib:$WINEXINSTALLDIR/winex/bin:$LD_LIBRARY_PATH/lib32:/usr/lib32"

/my comments



I tested with World of Warcraft, Half Life 2/Steam and a few other win32 games I had on my hard drive, everything appears to be working great. 

So far I have only tested Dungeon Siege with it but it worked going to test it with some other games when i get out of work.
Hope this helps for others.

Running it on a Compaq R3000 Laptop Nvidia Gforce 440 go 512mb ram and 64bit Kubuntu

---

### Post by janesy on 2005-04-20
thanks, i will give that a go! and thank you again :)

---

### Post by brad.arth on 2005-05-15
Where are you obtaining the package files?

---

### Post by Muchacho_Gasolino on 2005-05-15
gotta pay for a subscription on transgaming.com  ;-)

---

### Post by brad.arth on 2005-05-16
I wish they had a 30-day trial, because Im just learning linux and am giving it a test-run, to see if its a viable windows replacment. I don't feel like paying money for apps I may never use more than once. I guess I may have to wait until it's available as a trial or free through compiling.

---

### Post by slux on 2005-05-16
There used to be a trial version but it seems to have disappeared. Maybe if you emailed them about it, they'd at least shed light on why it's no longer offered.

That said, you can definitely try most of the Cedega technology if you compile ReWind or you could test plain wine with dx9 patches.

There's also the option of using shady means to get a copy and just test it of course but that one may or may not be acceptable to you personally. :)

---

### Post by brad.arth on 2005-05-16
After you've downloaded the .deb files to install, why would you pay for a subscription? What other services would they offer?

---

### Post by jdodson on 2005-05-16
[QUOTE=brad.arth]After you've downloaded the .deb files to install, why would you pay for a subscription? What other services would they offer?[/QUOTE]

more game support later.  bugfixes, patches, etc.

---

### Post by drews_blunted on 2005-05-18
[QUOTE=janesy]
has any one got cedega and CS working using the 64bit kernal?

thanks

dave
[/QUOTE]

Yep ive got CS and Steam working great even HL2  :-|

---

