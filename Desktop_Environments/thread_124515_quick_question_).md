---
title: "quick question :)"
date: 2006-02-01
forum: Desktop Environments
---

### Post by Patrick-Ruff on 2006-02-01
sup all, well Ubuntu has worked out well for me.  however, I Just need to know one thing, how do I connect using my dial modem?  I've got drivers for it and all that and I don't think that will be an issue but I set up a connection using pppconfig and now I don't know how to use it.  reply quick please. (sorry I didn't feel like reading through hours of stuff)

---

### Post by super on 2006-02-01
try this: system->administration->networking. select 'dial-up networking/ppp' and click 'configure'. you should be able to just fill in the information. when it asks for a location of the modem the most common is /dev/modem. the critical part is if your modem is supported by linux or not. many 'win/softmodems' are not.

if your modem is a softmodem it gets a bit trickier.
visit 'linmodem' for supported modems and their drivers. download and install with the given instructions. if that still doesn't work, download 'scanmodemhere' (you may need to download this in windows then copy it in linux) and run it from the terminal.

it will report the make of modem in the file called modem**.txt in the same place where ur scanmodem script is.

If u cant still make out, send them your modems1.txt to [http://linmodems.technion.ac.il/first.html](http://linmodems.technion.ac.il/first.html) and they can give you better instructions.

---

### Post by Patrick-Ruff on 2006-02-01
sorry that wasent what I asked.  I can do  ```
pon
```  and it will open the modem port (I can hear it on the speakers)  but HOW do I dial it???

is it ```
pon (name of connection)
```?

---

### Post by Gcool on 2006-02-01
You can for example install gnome-ppp for this. That will give you a graphical interface to configure your connection (dialing number, username,...) + the possibility to connect.

---

### Post by Patrick-Ruff on 2006-02-01
how would I go about doing that?

---

### Post by Gcool on 2006-02-01
sudo apt-get install gnome-ppp

---

### Post by Patrick-Ruff on 2006-02-01
after typing that in I got a message... (NOTE:I'm on Hoary Hedgehog 5.04)
E: could not get lock /var/lib/dpkg/lock - open (11 resource temporarily unavailable) 
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?)

---

### Post by Gcool on 2006-02-01
Make sure you don't have synaptic or software update opened, when you try to do this.

---

### Post by Patrick-Ruff on 2006-02-01
heh lol.  I did it but now it says
E: Couldn't find package gnome-ppp

---

### Post by Gcool on 2006-02-01
Ok, try this:

* Make sure your ubuntu cdrom is placed in the drive
* sudo apt-cdrom add
* sudo apt-get update
* sudo apt-get install gnome-ppp

---

### Post by Patrick-Ruff on 2006-02-01
still says couldn't find package..

---

### Post by Gcool on 2006-02-01
Ok, lets do it in another way:

* Download the gnome-ppp package [here]("http://www.gnome-ppp.org/download/0.3/gnome-ppp-0.3.21.tar.gz")
* tar -zxvf gnome-ppp-0.3.21.tar.gz
* ./configure
* make
* sudo make install

---

### Post by Patrick-Ruff on 2006-02-01
k dling now, my iPod has come majorly in handy these past few days :D

---

### Post by Patrick-Ruff on 2006-02-01
w8 thats as confusing as hell, can you walk me through it?  I AM a noob lol.

---

### Post by Gcool on 2006-02-01
So you put the tar.gz file in your home directory for example. Then you type the following in console:

* tar -zxvf gnome-ppp-0.3.21.tar.gz (this wil "unzip" the package)
* cd gnome-ppp-0.3.21 (a folder with this name will have been created)
* ./configure (this can take a few moments. If something's wrong, it'll give you an error msg at the end)
* make (to compile the progam, can also take a few moments)
* sudo make install (to install it)

If this all happens succesfully, then type gnome-ppp in console, and the program should open.

---

### Post by Patrick-Ruff on 2006-02-01
it had that error.  after running ./configure it said 
```
 no acceptable C compiler found in $PATH
see 'config.log' for details.
```

---

### Post by Patrick-Ruff on 2006-02-01
this is turning out to be a not so quick question.  anyone know???

---

### Post by danish_demon on 2006-02-01
this is a fellow noob responding so take what i say with a grain of salt.  do you have gcc and g++ installed?  if not go to synaptic and search for "gcc" and install gcc-4.0 and then search for "g++" and install whatever version of g++ it provides with the highest version number.  

**i think** that will solve this aspect of your problem (the no C compiler found).

---

### Post by Patrick-Ruff on 2006-02-01
great... well I have yet another problem.  I fixed it a few days ago but apparently deleting the DNS "local" hosts started it up again.  a fellow on Yahoo chat told me a code that fixed it.  it was like adding local hosts to fix the problem because it said couldn't connect and then it said "adding eclypse (my computer name) to /etc/hosts/ may fix this problem"

whats the code??

---

### Post by danish_demon on 2006-02-01
that i cannot help you out with, but i'm sure somebody around here knows what you are referring to.

---

### Post by Patrick-Ruff on 2006-02-04
ok back to it people.  help me figure this out here.

---

