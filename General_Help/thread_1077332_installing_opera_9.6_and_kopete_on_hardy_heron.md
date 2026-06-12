---
title: "installing opera 9.6 and kopete on hardy heron?"
date: 2009-02-22
forum: General Help
---

### Post by bilmas on 2009-02-22
on the opera website there is a version available for ubuntu 8.04 but when downloaded and ran through the package installer i'm given the error: dependency is not satisfiable

i am also unable to find a version of kopete for hardy heron and i'd prefer this software to pidgin

thanks in advance for the help!

---

### Post by kmac on 2009-02-22
Allow third-party software sources and then

```
sudo apt-get install opera kopete
```

---

### Post by bilmas on 2009-02-22
> **kmac said:**
> Allow third-party software sources and then

```
sudo apt-get install opera kopete
```


sorry i am brand new to linux of any kind.  how do i make those changes?

---

### Post by kmac on 2009-02-22
Open a terminal by going to

Applications -> Accessories -> Terminal

Then type that command in there and hit enter. You will then be prompted for a password. Enter YOUR user password (this is Ubuntu's way of saying "are you sure, mate?" and is also used for various security reasons). Once the installation is done, you should be able to find both programs under 

Applications -> Internet -> ::Program::

---

### Post by bilmas on 2009-02-22
> **kmac said:**
> Open a terminal by going to

Applications -> Accessories -> Terminal

Then type that command in there and hit enter. You will then be prompted for a password. Enter YOUR user password (this is Ubuntu's way of saying "are you sure, mate?" and is also used for various security reasons). Once the installation is done, you should be able to find both programs under 

Applications -> Internet -> ::Program::

hrm i entered that and this is what i got:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate
david@david-desktop:~$ 


---

### Post by kmac on 2009-02-22
Ok then we'll keep this simple...

[http://www.opera.com/download/index.dml?platform=linux](http://www.opera.com/download/index.dml?platform=linux)

And then Kopete should still be in native Repos

```
sudo apt-get install kopete
```

---

### Post by bilmas on 2009-02-22
> **kmac said:**
> Ok then we'll keep this simple...

[http://www.opera.com/download/index.dml?platform=linux](http://www.opera.com/download/index.dml?platform=linux)

And then Kopete should still be in native Repos

```
sudo apt-get install kopete
```

that's where i tried getting opera from as it doesn't even appear in the synaptic package manager when searched for

entering the kopete command line got me this:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kopete


---

### Post by kmac on 2009-02-22
Have you tried 

Applications -> Add/Remove

Then switch the dropdown box to "all available applications" and search for either program?

---

### Post by ashwinhgtx on 2009-02-22
> **bilmas said:**
> hrm i entered that and this is what i got:

Do this after you have edited the sources.
```
sudo apt-get update
```

Then try to install Opera again.
```
sudo apt-get install opera
```

---

### Post by bilmas on 2009-02-22
> **kmac said:**
> Have you tried 

Applications -> Add/Remove

Then switch the dropdown box to "all available applications" and search for either program?

i just tried to install opera and this is what i got:

```
Opera cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.
```

---

### Post by ashwinhgtx on 2009-02-22
> **bilmas said:**
> i just tried to install opera and this is what i got:

```
Opera cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.
```

Paste the output of this command.

```
uname-a
```

---

### Post by bilmas on 2009-02-22
> **ashwinhgtx said:**
> Paste the output of this command.

```
uname-a
```

in terminal?

---

### Post by kmac on 2009-02-22
> **bilmas said:**
> in terminal?

Yes sir.

---

### Post by bilmas on 2009-02-22
> **kmac said:**
> Yes sir.

```
david@david-desktop:~$ uname-a
bash: uname-a: command not found
david@david-desktop:~$ 

```

---

### Post by kmac on 2009-02-22
> **ashwinhgtx said:**
> Paste the output of this command.

```
uname-a
```

Sorry, he meant 

```
uname -a
```

with a space.

---

### Post by bilmas on 2009-02-22
```

Linux david-desktop 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux
```

---

### Post by ashwinhgtx on 2009-02-22
> **kmac said:**
> Sorry, he meant 

```
uname -a
```

with a space.

Sorry about that typo :-#

---

### Post by bilmas on 2009-02-22
> **bilmas said:**
> ```

Linux david-desktop 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux
```
any diagnosis on this one?

---

### Post by slidersv on 2009-03-16
> **bilmas said:**
> any diagnosis on this one?

Yes, I have the same problem.
I am getting this message when trying to install through "Add/Remove":


```
Opera cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.
```

I have
atlas@u238:~$ uname -a
Linux u238 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
on Lenovo T61 and don't understand this error.

---

### Post by beau420 on 2009-03-22
I had the same problem using Add/Remove Programs from the menu.  Tried to Add it...gave me a popup asking me to enable a third party install....I said sure....then gave me the same error:

Opera cannot be installed on your computer type (i386)

Same error when installing from terminal:

michael@michael-desktop:~$ sudo apt-get install opera
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate

michael@michael-desktop:~$ uname -a
Linux michael-desktop 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux

So I went to [http://www.opera.com/download/index.dml?platform=linux](http://www.opera.com/download/index.dml?platform=linux) and downloaded Opera...ran .deb file...opened installation installed fine.  Might be the mirror for Opera package or Opera has a newer install

---

