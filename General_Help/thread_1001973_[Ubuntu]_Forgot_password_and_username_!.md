---
title: "[Ubuntu] Forgot password and username !"
date: 2008-12-04
forum: General Help
---

### Post by retskrad on 2008-12-04
Just installed Ubuntu with Wubi and when i restart to use Ubuntu, I get to the login screen and I must write in my username and passs.. I cant remember my username and pass when I installed in Wubi... What should I do? Is there a way to get it?

---

### Post by Jammanuser on 2008-12-04
> **retskrad said:**
> Just installed Ubuntu with Wubi and when i restart to use Ubuntu, I get to the login screen and I must write in my username and passs.. I cant remember my username and pass when I installed in Wubi... What should I do? Is there a way to get it?

uh oh...THAT'S not good! ;) there are such things as password recovery tools...but not sure right now which one you'll need...will come back when i obtain more info!

Cheers! :)

-jammanuser

:D

---

### Post by sisco311 on 2008-12-04
[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by Jammanuser on 2008-12-04
> **sisco311 said:**
> [http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

Hey, cool!!! sisco...i didn't know u could do that, with the recovery mode! but wait...doesn't that mean that **anyone** can get into Ubuntu on ur computer, with the same method??? ;)

Looking forward to ur reply...

-jammanuser

:D

---

### Post by retskrad on 2008-12-04
> **sisco311 said:**
> [http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

Didnt work, you could only change UNIX PASSWORD, IT DIDNT REGONIZE THE COMMAND username.

---

### Post by Jammanuser on 2008-12-04
> **retskrad said:**
> Didnt work, you could only change UNIX PASSWORD, IT DIDNT REGONIZE THE COMMAND username.

well...that's WHY!!! :D u need to replace "username" with the name u want ur username to be!

Cheers! ;)

-jammanuser

:D

EDIT: in order to reset ur password, u need to type

```
passwrd *username*
```

where "username" should be replaced with with the username you want to reset! However, since the tutorial doesn't specify whether or not you need to know what ur username was (i.e. the one that u had before!), i'm not sure **exactly** what they mean by replacing it with the username you want to reset! It could be, u DO need to know ur previous username, in order to reset ur password, in which case if u forgot it, then you won't be able to reset it with this particular method, and you'll need to try something else! Cheers!

---

### Post by sisco311 on 2008-12-04
> **retskrad said:**
> Didnt work, you could only change UNIX PASSWORD, IT DIDNT REGONIZE THE COMMAND username.

first type:
```
ls /home
```this command should print your user name (login name)
ex.:

```
ls /home
retskrad
```

then:
```
passwd *retskrad*
```

---

### Post by Jammanuser on 2008-12-04
> **sisco311 said:**
> first type:
```
ls /home
```this command should print your user name (login name)


oh...ok!!! so THAT'S how it works!!! i didn't understand before that "ls /home" reveals the username! that was the missing piece of information...and u cleared it up for me! Thanks! 

Cheers! ;)

-jammanuser

:D

---

### Post by magmon on 2008-12-04
I recommend writing it down this time xD. I use my first name and universal pass, easy to remember.

---

### Post by sisco311 on 2008-12-04
> **Jammanuser said:**
> Hey, cool!!! sisco...i didn't know u could do that, with the recovery mode! but wait...doesn't that mean that **anyone** can get into Ubuntu on ur computer, with the same method??? ;)

Looking forward to ur reply...

-jammanuser

:D

once you have physical access to a computer, no OS is secure.

for example if you boot a live cd you can access the data on the hard disk.

EDIT:

i've found this thread in the Recurring Discussions subforum: [http://ubuntuforums.org/showthread.php?t=989517]("http://ubuntuforums.org/showthread.php?t=989517")



EDIT2:

happy Day of the Ninja!

---

### Post by Jammanuser on 2008-12-04
> **sisco311 said:**
> once you have physical access to a computer, no OS is secure.

for example if you boot a live cd you can access the data on the hard disk.

EDIT:

i've found this thread in the Recurring Discussions subforum: [http://ubuntuforums.org/showthread.php?t=989517]("http://ubuntuforums.org/showthread.php?t=989517")


Thanks for the link...it really helped a LOT!!! now i understand a lot more on just how many security holes Ubuntu REALLY has... :D i think i'm going to go ahead and password protect my recovery mode! ;)

Cheers!

> **sisco311 said:**
> 
EDIT2:

happy Day of the Ninja!

:D :D :D :D :D

---

### Post by Jammanuser on 2008-12-06
> **magmon said:**
>  I use my first name and universal pass, easy to remember.

yes...but that's a pretty insecure password!!! ;) a **strong** password needs to have at LEAST 10 characters (all of mine r 14 though!:))...and keep in mind that the password is even stronger, if u **combine** uppercase and lowercase letters! and if u add a couple of numbers, or perhaps special characters...it would take YEARS to crack!!! ur current password wouldn't last five MINUTES with a mildly skilled hacker! ;)

Take a look at these figures {pay **particular** attention to the difference between using only lowercase characters and using all possible characters (uppercase, lowercase, and special characters - like @#$%^&*). Adding just one capital letter and one asterisk would change the processing time for an 8 character password from 2.4 days to 2.1 centuries)}:

```
**_Password Length_**	     **_All Characters_**	          **_Only Lowercase_**
3 characters        0.86 seconds                  0.02 seconds
4 characters        1.36 minutes                  .046 seconds
5 characters        2.15 hours                    11.9 seconds
6 characters        8.51 days                     5.15 minutes
7 characters        2.21 years                    2.23 hours
8 characters        2.10 centuries                2.42 days
9 characters        20 millennia                  2.07 months
10 characters       1,899 millennia               4.48 years
11 characters       180,365 millennia             1.16 centuries
12 characters       17,184,705 millennia          3.03 millennia
13 characters       1,627,797,068 millennia       78.7 millennia
14 characters       154,640,721,434 millennia     2,046 millennia 

```
My source? You can find it [HERE]("http://onemansblog.com/2007/03/26/how-id-hack-your-weak-passwords/")!!! ;)

Cheers! :)

-jammanuser

:D

EDIT: i also use Roboform (a password storing program that **encrypts** its stored passwords!) for my passwords, and so don't need to memorize every single one! The program is a really neat Windows program that attaches itself to ur browser, and only requires ONE master password (which u need to memorize...although u can still keep it simple and still remain secure!) to access its stored passcards! its also really neat in the fact that a single click auto-fills in username/password fields on webpages...and also has a built-in password generator in which u can choose how many characters to use! Bottom line: its really neat, and simple to use! Cheers! xD :D

---

### Post by ditto1958 on 2009-01-04
I tried to get into my Xubuntu computer today (actually, it's a dual boot with XP) and I couldn't remember my user name or password. I tried the way that is discussed here by going to the recovery mode, but somehow I seem to have screwed up. 

When I go there it lists my username as *ditto1958[I]*[/I]. When I tried putting that in, though, to change the password, it would not accept all the letters.

Now I think I've screwed everything up, because if I try to log in at the normal screen, the only usernames that are available are "ditto" and "ditto5." I tried to set new passwords for those usernames, but it won't accept them.

Now what do I do?

---

