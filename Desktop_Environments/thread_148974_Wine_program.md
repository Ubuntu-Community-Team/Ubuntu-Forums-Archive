---
title: "Wine program"
date: 2006-03-23
forum: Desktop Environments
---

### Post by cobbweb on 2006-03-23
Hi, 
  I just did a 


```


 sudo apt-get install wine

```


and 

```

sudo apt-get install xwine


```

to install wine. I just cant figure out how to use it. How do you use wine? I havent been able to find where you open the program from, and im a little flustered..... Any ideas where i could find the programm or if im missing somthing? Thank you, any help is wanted,

 Cobbweb

---

### Post by aysiu on 2006-03-23
This may be a good start:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by JoshHendo on 2006-03-23
Just a few things. Err, I don't think that you can have wine and xwine. If you install xwine with wine installed, it will remove wine. Still, install wine, and you can use that. Right click on the file you wish to open in wine, select "Open with other application", and then in the custom application box, type in wine. That will then open that file with wine. If you want, you can open up the terminal, go to the folder that contains the file you want to open, then type in "wine FileName.exe" (no quotes, replace FileName.exe with the name of the file you wish to open with wine). This will run it, and if it doesn't work properly, or doens't close when you want it to, you can just close the terminal. That sometimes happens when using wine.

---

### Post by cobbweb on 2006-03-23
hey wine works great now, just one thing. When ever I open the exe it wants to install it over and over again (every time I do wine program.exe) I installed itino the c/: drive in the emulator, but where is that on linux? 

 Thanks 

 cobbweb



 Problem fixed, this is what I do now: 
  When it install's it, It will reconize your linux partions so just make a folder for all the files you install that are windows files and install them into that forlder (this folder locatd somewhere on your linux partion) then just make a link and magic. It works. 

 Thanks for all the help

---

### Post by JoshHendo on 2006-03-23
C Drive is a virtual folder in your home folder.

Well, you can't find it becuase your not supposed to, as it is hidden.

Press ctrl-H in your home folder and look for a file names .drive_c or soemthing similar to that.

---

