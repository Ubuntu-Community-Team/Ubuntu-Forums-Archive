---
title: "Don't type sudo chmod 700 /home  !!!"
date: 2006-03-01
forum: Desktop Environments
---

### Post by JungleBeast on 2006-03-01
I'm new to this stuff, and was just feeling like i could type things into terminal without copying and pasting from the help files when i typed: 
```
sudo chmod 700 /home
```
Bad move!   :-# :( 

 so managed to get back into the system using failsafe terminal - what a good idea that failsafe terminal is! i was wondering what that "session" box was for!     almost thought i was gonna have to reinstall ubuntu! 

So could anyone tell me what "chmod" /home should be?   I've got it set to 777

Also, can anyone help me solve my original problem: how to make my whole home folder not readable by the network on samba? ( and then pick specific files,   ie. my mounted windows fat32 drive ? )

Thank you oh wise and knowledgeble linux gods :-D

---

### Post by engla on 2006-03-01
777 not a good idea either! Any user on the system will have write permissions to /home, meaning they can add and remove files at will.

My home is here:
drwxr-xr-x    6 root root 4,0K 2006-02-11 19:00 home/

I haven't changed it so the default permissions are 755 (rwx, rx, rx)

---

### Post by Ramses de Norre on 2006-03-01
The first number is the owner of the file, the second the group of the owner, the third everyone else.
The numbers are the sum of the codes for the permissions: 1 = execute; 2 = write; 3 = read.
so chmod 777 gives everyone all rights, chmod 700 gives the owner all rights, no one else can do anything with the file and you can make every combination like that.

---

### Post by JungleBeast on 2006-03-02
Cheers Engla, i'll change mine back to 755 then.  :D  


So Ramses, I don't quite follow, 5 is rx   =  3 + 1  ?    and how do you get to 7 by only adding 3 + 2 + 1 ?    I don't think I've understood what you are saying yet  :-k    

So to make a folder that's not readable to others on the network, would I type:     chmod 770   ?    

Thanks again  :)

---

### Post by aamukahvi on 2006-03-02
[QUOTE=JungleBeast]Cheers Engla, i'll change mine back to 755 then.  :D  


So Ramses, I don't quite follow, 5 is rx   =  3 + 1  ?    and how do you get to 7 by only adding 3 + 2 + 1 ?    I don't think I've understood what you are saying yet  :-k    

So to make a folder that's not readable to others on the network, would I type:     chmod 770   ?    

Thanks again  :)[/QUOTE]
It's
r w x
4 2 1

---

### Post by linuxden on 2006-03-02
Ramses was right on the principle system... the numbers wiork like so:

                 user          
read   write   execute    
400     200      100         

             Group          
read   write   execute    
40     20      10       

             other        
read   write   execute    
4         2          1     

you just add the numbers up...

Sorry for the weird graph i am doing CUPS research at the moment... ;o)

edit: Amukhavi you got there 1st... ;o)

---

### Post by Ramses de Norre on 2006-03-02
Typo, the 3 must be 4 :)

---

### Post by svenforum on 2006-03-02
Why 1, 2, 4?
2^0 = 1
2^1 = 2
2^2 = 4

more information at
$ man chmod

---

### Post by Ramses de Norre on 2006-03-02
Because every value you get from adding those three stands for a unique combination of them, you can't combine them on another way and get the same outcome.
And it are indeed the first three binary size orders. (is that a correct word?)

---

### Post by akiro.yamamoto on 2006-03-02
/home is typically 755 and /home/user 700
At least that's how it is on my system ;)

---

### Post by JungleBeast on 2006-03-02
Thanks everyone! \\:D/ 

That's all crystal clear now, even understand both the human and binary logic behind it now!  
And thanks Akiro for your pointer on what i need, that's perfect!
:mrgreen:

---

### Post by Seaniesean on 2008-06-20
Um, i just did the same thing (typed sudo chmod 700/home).

And now, i can only use failsafe terminal...

I was only trying to correct some error message on login about "should have 655 permissions" or something.

I'm sorry to bump old threads.  Can someone tell me exactly how to be able to login again?  I don't really care about the error at start anymore...but if you'd like to tell me how to correct that too, i'd be much obliged.

---

### Post by sisco311 on 2008-06-20
> **Seaniesean said:**
> Um, i just did the same thing (typed sudo chmod 700/home).

And now, i can only use failsafe terminal...

I was only trying to correct some error message on login about "should have 655 permissions" or something.

I'm sorry to bump old threads.  Can someone tell me exactly how to be able to login again?  I don't really care about the error at start anymore...but if you'd like to tell me how to correct that too, i'd be much obliged.

type:
```
sudo chmod 0755 /home
```and
```
chmod 0644 ~/.dmrc
```in the failsafe terminal.

---

### Post by Seaniesean on 2008-06-20
Thanks a lot mate!  Good to have it clear and simple...

Wait a minute, that just sounds far too easy!  

I will be so happy if that works!

---

