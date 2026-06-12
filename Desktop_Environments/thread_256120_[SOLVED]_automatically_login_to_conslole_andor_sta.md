---
title: "[SOLVED] automatically login to conslole and/or start X xorg"
date: 2006-09-12
forum: Desktop Environments
---

### Post by Markkreuzz on 2006-09-12
Hello, If there is anyone here that could tell or even give me a link on how to login to X automatically after Dapper is finished booting - i am using Dapper 6.06.1 LTS... help puhleezzzz
--

The story starts like this. I did a server install on my old PII pc and it is working great. I also did apt-get install x-common fluxbox and everything installed just fine. 

And now my problem is... i find annoying to login to the console and typing in startx everytime my pc boots up. ive also tried apt-get install xdm... and now it get's more annoying as the graphical logon is there and i tried logging in and doesn't log me in. now if there is anyone here that could help me or even just point me in the correct direction I would be eternally grateful...    \m/.

Here are my other info... 
pII-333 256MB
xubuntu 6.06.1 LTS Dapper server install
fluxbox
xorg 
xdm
================================================================

For those people who just passed by and does't like to click on links

Here's what ive done: ***this is from peekpt and the thread can be found [here]("http://ubuntuforums.org/showthread.php?t=31310")



**[SIZE="3"]This guide let's you have autologin and autostart for your XFCE:  [/SIZE]** 
****in my case xserver*

Let's open a console and then create the file autologin.c


Code:
```
sudo nano autologin.c
```
and paste this code inside (middle mouse button will paste the text you underline):


Code:
```
int main() {
     execlp( "login", "login", "-f", "your_user_here", 0);
 }
```replace the string: your_user_here with the user you want to autologin. (ctrl+X to save) btw, use your prefered editor.

Let's compile.. you will need to have gcc installed:


Code:
```
sudo gcc -o autologin autologin.c
```
copy the compiled autologin file into /usr/local/sbin


Code:
```
sudo cp autologin /usr/local/sbin
```now we need to edit the file /etc/inittab


Code:
```
sudo nano /etc/inittab
```
search for this:


Code:
```
1:2345:respawn:/sbin/getty 38400 tty1
```
put a # to comment this line and add this new line:


Code:
```
1:2345:respawn:/sbin/getty -n -l /usr/local/sbin/autologin 38400 tty1
```it will look like this:

Code:
```
#1:2345:respawn:/sbin/getty 38400 tty1
1:2345:respawn:/sbin/getty -n -l /usr/local/sbin/autologin 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
```this will make the autologin stuff...



let's make the autostart:


Code:
```
nano .bash_profile
```put this code on the bottom and save it


Code:
```
if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
    startxfce4
fi
```
*****note: i used startx instead startxfce, you could also do /usr/bin/path-to-your-desktop-of-choice-binary *

then you just have to remove your login manager :

Code:
```
sudo apt-get remove gdm xdm kdm
```
reboot your machine

---

### Post by moore.bryan on 2006-09-12
*check out [http://doc.gwos.org/index.php/Automatic_Login_No_Authentication](http://doc.gwos.org/index.php/Automatic_Login_No_Authentication).  i think this is what you're looking for.*

---

### Post by bswilson on 2006-09-12
I think if you'll install the ubuntu-desktop package, it will give you what you need.  Should set the login configuration and everything...

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Markkreuzz on 2006-09-13
Thanks for the replies guys. ill look into the how-to and will try it later, still busy at work...oh well...

---to Bwilson,thanks for the reply also, but if i were to do that, i would've just installed ubuntu. and also it would make my p-II 333 mhz pc crawl to a stand still and basically make it useless. i really love fluxbox and all the transparent menus and all... so i'm very happy, it's just figuring out that minor boot up thing is really taking a lot of my time and brain cells.

Also the reason i want it to start and log me in after boot up - is also to automatically start my .torrent downloads since i leave my pc on while im at work. Thanks

---

### Post by moore.bryan on 2006-09-13
[I]just as a side note, have you tried openbox?  i tried out both fluxbox and ob, went with ob, and never looked back...
[http://www.icculus.org/openbox/](http://www.icculus.org/openbox/)
[/I]

---

### Post by Markkreuzz on 2006-09-13
Thanks for the info moore.bryan ... also while i was also looking around i found the same guide here [http://ubuntuforums.org/showthread.php?t=31310]("http://ubuntuforums.org/showthread.php?t=31310") hah! O_o i just didn't type in the correct keywords in the search box.
i junked the XDM and now i am a very happy person.... 
...*hmmm *openbox.... i think i'll give it a spin.... well on to a new problem...

---

