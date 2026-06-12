---
title: "question about install Tor-0.2.1.24"
date: 2010-03-06
forum: Desktop Environments
---

### Post by tonjaa on 2010-03-06
karmic 9.10 64 bit
i download program Tor-0.2.1.24.tar.gz and i extract in folder downloads i try to install it.
i cd to folder Tor-0.2.1.24  and use ./configure  it's checking to end config.status . 
and then how i command it for install and run this program?

---

### Post by kleskjr on 2010-03-06
usually u should run

make
sudo make install

but I recommend you to install it through the synaptic
there u can install vidalia, a very usefull gui

---

### Post by tonjaa on 2010-03-06
it's have error

---

### Post by tonjaa on 2010-03-06
after i use command make and make install i install vidalia from synaptic but it have error starting Tor when i run vidalia 
it's show fonts like dots i can't read . how i can fix it?
i got this

---

### Post by kleskjr on 2010-03-06
Ohh it looks weird.
Probably I would uninstall tor manually from the konsole and vidalia from synaptic. And then install both tor and vidalia from the synaptic. Hope it works

---

### Post by tonjaa on 2010-03-06
i try to reinstall Tor from web [https://www.torproject.org/docs/debian.html.en](https://www.torproject.org/docs/debian.html.en)
by step for ubuntu 9.10 and install vidalia from synaptic
it's no error but has problem about font same time can't read . i don't know this is bug 
or have something wrong .

---

### Post by kleskjr on 2010-03-07
seeing the picture you have attached it seems that the tor is working and is connected (because u have a green onion). if you do not insist to use the gui probably you can use it the way is now. all the settings you need can be entered here

/home/USER/.vidalia/torrc

(at least on my machine but definitely you have somewhere the torrc file)

good luck

---

### Post by tonjaa on 2010-03-08
how i can do with torrc ?
what 's command for use ?

---

### Post by kleskjr on 2010-03-08
first u have to find the file torrc 
in my system it is  in /home/USER/.vidalia/torrc

then you can access it with any text editor
ie: sudo gedit /home/USER/.vidalia/torrc

in the file you can set your ports and a few more things.

but again, it seems your tor is working. how do you use it? with tor button add-on in firefox? if yes you can turn on the button and test if it really works

---

