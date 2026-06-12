---
title: "How I compiled qjoypad on AMD64 Fiesty"
date: 2007-09-27
forum: Gaming &amp; Leisure
---

### Post by flinkdeldinky on 2007-09-27
First I went to to:  [http://qjoypad.sourceforge.net/#download]("http://qjoypad.sourceforge.net/#download") and downloaded the file called qjoypad-3.4.1.tgz and placed it in a directory within my home directory.  In my case it was games/Linux.

From a terminal, in my case Konsole, I ran the following command:
tar -xzvf qjoypad-3.4.1.tgz 

Now I want to make a symbolic link so that when I compile the program it can find the Xtst library.  I do this with the following command in a terminal:
sudo ln -s /usr/lib/libXtst.so.6.1.0 /usr/lib/libXtst.so 

Then I cd into the qjoypad source code directory:
cd qjoypad-3.4.1/

and Read the file README.txt:
less README.txt 

and follow the directions from there.  I installed it in my home directory so when I ran ./config it looked like:
./config --prefix="/home/myusername/games/Linux/qjoypad"

You will have to make the install directory prior to running the ./config --prefix  command.

Hope this helps somebody.

PS. I forgot to mention that I'm running Kubuntu and that qjoypad requires QT libraries, but I don't think it requires KDE. I just remapped the Marathon's keyboard controls to my no name USB gamepad and qjoypad really does work well.  This program should be in the repositories.

---

### Post by cx23 on 2009-03-04
If you are using Ubuntu 8.10 or later you will need qt3 libraries in order to install and use qjoypad and compile it yourself. It is pretty straightforward.

Here is how I installed it on Ubuntu 8.10 (Intrepid) amd64:

1) install qt3 by running this command in the terminal
$ sudo apt-get install qt3-apps-dev

2) [http://qjoypad.sourceforge.net/](http://qjoypad.sourceforge.net/). download qjoypad-3.4.1.tgz and extract it:
$ tar -xzvf qjoypad-3.4.1.tgz

3) Change directory to the qjoypad source code directory:
$ cd qjoypad-3.4.1/src

3a) gedit file loop.cpp. find the line "usleep(1)" and change it to "usleep(10000)". Save the file. That will force qjoypad using less CPU time.
$ gedit loop.cpp

4) Compile it
$ config && make

5) If there were no errors just install into /usr/local/bin 
$ sudo make install

6) run it
$ qjoypad

Later you can edit your applications menu and create a new entry for qjoypad program.

Enjoy

---

### Post by dogen2 on 2009-03-29
Here is a deb compiled for AMD64 9.04 Jaunty Jackelope Beta

---

### Post by SpencerOKrum on 2009-05-07
> **flinkdeldinky said:**
> 
Now I want to make a symbolic link so that when I compile the program it can find the Xtst library.  I do this with the following command in a terminal:
sudo ln -s /usr/lib/libXtst.so.6.1.0 /usr/lib/libXtst.so 


Hope this helps somebody.


Flinkdeldinky, this part was key.  I encountered an error when make couldn't find lxtst. I was able to make qjoypad 3.4.1 work on my acer aspire one A110 running debian squeeze. 

Really neat program.
Thanks
Spencer

---

