---
title: "run script on boot up?"
date: 2006-07-04
forum: Desktop Environments
---

### Post by karlsson88 on 2006-07-04
Hi!

how do i get this line to run everytime i boot up? so i don't have to type it in a Terminal to get my mouse working as it should.

> xmodmap -e "pointer = 1 2 3 7 6 4 5 8 9 10 11"


i have tried to put it in the "sessions" thing but that didn't do it. ?

---

### Post by frodon on 2006-07-04
To run your script on startup do as follow :
1- create a file under init.d : sudo gedit /etc/init.d/my_script
2- put your command lines/script in the file & save it
3- make the file executable : sudo chmod +x /etc/init.d/my_script
4- make it run on boot : sudo update-rc.d my_script defaults

That's all

---

### Post by jimbob on 2006-07-04
Try putting it in /etc/rc.local and see if that will work for you.

 There is probably a better place but I have forgotten which.

EDIT: Oops - better solution snuck in on me ...
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by frodon on 2006-07-04
For information the goal of the "update-rc.d" command is to create the rc.local symbolic links of a script located under init.d depending on the priority level you set.
Another way to do it is to put your script under init.t then use BUM : 
[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

---

### Post by tomchuk on 2006-07-04
xmodmap needs an X display to connect to to run, putting the xmodmap command in an init script or rc.local will fail every time.

Gnome session will automatically look for a ~/.Xmodmap file to run when X starts. Just put the following into ~/.Xmodmap :
```

pointer =1 2 3 7 6 4 5 8 9 10 11

```
Next login you should get a message asking if you want to load the file.

---

