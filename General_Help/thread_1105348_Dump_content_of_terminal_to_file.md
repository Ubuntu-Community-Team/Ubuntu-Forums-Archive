---
title: "Dump content of terminal to file"
date: 2009-03-24
forum: General Help
---

### Post by dannyboy0110 on 2009-03-24
Hey, this might sound like a ridiculous question but i was wondering if there is a way to dump the readout from a terminal to a text file.
I am currently running ubuntu 8.10 and also use imsniff to log the msn chatter from computers on the network. However i need some way of saving the readout, preferably as the programme runs, to save having to copy and paste all the information
thanks for taking the time to read this and any help will be greatly appreciated


Dan =)

---

### Post by mhgsys on 2009-03-24
just put > nameoffileyouwant

f.e
sudo imsniff wlan0 > bla

would give a file called bla.

---

### Post by dannyboy0110 on 2009-03-24
knew id sound like a noob. lol
and its that easy?
thanks for your help
going to hold my head in shame now =)

Dan

---

### Post by balloooza on 2009-03-24
Well, there is two ways, if you are looking to dump the output of cammands you allready ran, just select the wanted text and past in to gedit (or somthing of that nature)

If you want to go all linux'y, when you type the command, you can simpily put a > at the end.... so
```
foo > output.txt
```
or..
```
sudo apt-get install -s firefox > output.txt
```
where output.txt i the filename, in the current directory (. means here ./ means right here, or you can say what directory /media/EXhrddrv/ etc.)

---

