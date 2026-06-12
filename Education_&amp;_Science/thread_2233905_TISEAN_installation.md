---
title: "TISEAN installation"
date: 2014-07-11
forum: Education &amp; Science
---

### Post by Nicola_Staffolani on 2014-07-11
Dear Ubuntu users,

I am trying to install in /home a program called [Tisean]("http://www.mpipks-dresden.mpg.de/~tisean/Tisean_3.0.1/index.html"); if u have a look at the webpage where they explain how to install it, they tell you you'll "probably" need to just run 3 commands:

> [COLOR=blue]./configure[/COLOR] --prefix=/my_home/Tisean_3.0.1
> [COLOR=blue]make[/COLOR] 
> [COLOR=blue]make install[/COLOR]

However, this is not the case in my case since I keep getting always the same error message when I run the 3rd command (> make install), that is:

make: *** [do_install] Error 1

which is not self-explanatory at all! It must be something that has to do with the --prefix, which - if I got it right - is where the executables are put...

Could somebody help me out?

Thank you in advance,

Nicola

---

### Post by tgalati4 on 2014-07-11
```
sudo make install
```

You can configure and make (compile) files locally, but to install them to the system requires root or sudo privileges.

---

### Post by steeldriver on 2014-07-11
It should be possible to run 'make install' without sudo **provided **you have specified the --prefix correctly at the configure stage - what exactly are you substituting for **my_home** when you run the command? Does the directory Tisean_3.0.1 exist there?

---

### Post by Nicola_Staffolani on 2014-07-14
Dear **tgalati4 **& **steeldriver**,

thank you very much both for your help!

I think steeldriver is right, indeed I have just [FONT=courier new]$ sudo make install[/FONT] but I've got the same message, and I agree again with steeldriver that the problem might be the prefix I am specifying... So, my home is simply [FONT=courier new]home[/FONT] I have downloaded the [FONT=courier new]tar.gz[/FONT] there. Afterwards, as explained [here]("http://www.mpipks-dresden.mpg.de/~tisean/Tisean_3.0.1/index.html"), I [FONT=courier new]$ gunzip TISEAN_3.0.1.tar.gz[/FONT] and then [FONT=courier new]$ tar -vxf TISEAN_3.0.1.tar[/FONT], so that now I have my folder [FONT=courier new]home/Tisean_3.0.1[/FONT]; now I go inside it, i.e. inside the folder [FONT=courier new]home/Tisean_3.0.1[/FONT] and do the following:

 [FONT=courier new]$ ./configure --prefix=/home/Tisean_3.0.1
$ make 
$ make install
[FONT=comic sans ms]
[/FONT][FONT=arial][FONT=comic sans ms]Can you find anything wrong? Should I remove the name of the Tisean folder from the prefix and just leave the name of my home folder? Thank you in advance!!

Nicola[/FONT]
[/FONT][/FONT]

---

### Post by Nicola_Staffolani on 2014-07-14
PS in the maenwhile that you reply, I have tried with:

[FONT=courier new]$ ./configure --prefix=/home
$ make 
$ make install[/FONT]

and the error message I have got is the following:

[FONT=courier new]$ /home/bin does not exist

[FONT=garamond]...[/FONT]
[/FONT]

---

### Post by Nicola_Staffolani on 2014-07-14
PPS for the sake of compliteness, what they write in their website, where you can download the software from, is:

 By default, the executables go to [COLOR=blue]$HOME/bin[/COLOR], you can change that to [COLOR=blue]mydir[/COLOR] by 

[INDENT]    > [COLOR=blue]./configure --prefix=mydir[/COLOR] 
[/INDENT]

---

### Post by coldraven on 2014-07-14
From here: [http://en.wikipedia.org/wiki/Home_directory#Unix](http://en.wikipedia.org/wiki/Home_directory#Unix)
> In Unix, a user will be automatically placed into their home directory upon [login]("http://en.wikipedia.org/wiki/Logging_%28computer_security%29"). The ~user  shorthand variable refers to a user's home directory (allowing the user  to navigate to it from anywhere else in the filesystem, or use it in  other Unix commands). 
The ~ ([tilde]("http://en.wikipedia.org/wiki/Tilde#Directories_and_URLs") character) shorthand command refers to that particular user's home directory.



So maybe you should try either ~home or the absolute path /home/nicola/
You would also probably have to create the directory /home/nicola/bin or whatever you choose to call it.

---

### Post by Nicola_Staffolani on 2014-07-14
> **coldraven said:**
> From here: [http://en.wikipedia.org/wiki/Home_directory#Unix](http://en.wikipedia.org/wiki/Home_directory#Unix)


So maybe you should try either ~home or the absolute path /home/nicola/
You would also probably have to create the directory /home/nicola/bin or whatever you choose to call it.

Dear coldraven,

thank you for replying! 

Regarding creating a new [FONT=courier new]bin[/FONT] directory, I thought I should use one of the following 4 (and not create a new one):
[LIST=1]
[*]/bin
[*]/usr/bin
[*]/usr/local/bin
[*]/home/Tisean_3.0.1/bin
[/LIST]

Which one of these 4? I say this because one usually doesnìt create a new bin folder each time he/she installs a program...

Nicola

---

### Post by steeldriver on 2014-07-14
$HOME and /home are not the same thing, you will not be able to write to /home without sudo permissions, whereas you have complete freedom to create whatever files you want in $HOME (which is a variable corresponding to your home directory, like /home/nicola). The tilde character ~ is a synonym for $HOME.

If you want all users of the computer to be able to use the Tisean software, you should probably install it to a location like /usr/local (i.e. use --prefix=/usr/local) - in that case you will need to use 'sudo make install'

If you want to install the software just for you - or you don't have sudo privileges - you should install to $HOME. It looks like the installer doesn't create the bin directory itself, so you will need to do something like

```

mkdir ~/bin

./configure --prefix=$HOME

make

make install

```

According to the info you posted, $HOME is the default install location - if that is the case you don't really even need to specify a --prefix value at all, but it will not hurt anything to be explicit. If ~/bin does already exist, mkdir will throw an error - which you can ignore.
 
Once the ~/bin directory exists, it will be added to your PATH next time you log in, so that any executables placed there will be found by the system.

---

### Post by Nicola_Staffolani on 2014-07-14
Hi steeldriver,

thank you very muc hfor your clear explanation! Unfortunately I have tried first to install the software for all users (used [FONT=courier new]--prefix=/usr/local[/FONT] & then '[FONT=courier new]sudo make install[/FONT]') but I've got the error message '[FONT=courier new]make: *** [do_install] Error 1[/FONT]'; afterwards I have tried to install the software for myself and I have therefore followed your instructions ([FONT=courier new]mkdir ~/bin[/FONT];  [FONT=courier new]./configure --prefix=$HOME[/FONT];  [FONT=courier new]make[/FONT];  [FONT=courier new]make install[/FONT]), but I've got again the same error message... Don't know what else to do...

Nicola

---

### Post by steeldriver on 2014-07-14
can you post some more lines of context around the do_install error please, and also the output of

```

ls -ld ~/bin

```

---

### Post by Nicola_Staffolani on 2014-07-14
unfortunately I cannot tell you more about the error message because '[FONT=courier new]make: *** [do_install] Error 1[/FONT]' is the only information that is printed out :mad: instead, if I type in: '[FONT=courier new]ls -ld ~/bin[/FONT]', then I get: '[FONT=courier new]drwxrwxr-x 2 nicola nicola 4096 Jul 14 14:39 /home/nicola/bin'...[/FONT]

---

### Post by steeldriver on 2014-07-14
Well I just downloaded it and it built fine on my Ubuntu 12.04 32-bit system

I suggest you start over and re-extract the archive in case any permissions or configuration settings have got messed up with the various install attempts. Having seen how many executable programs it splurges into ~/bin (76) I'm actually going to modify my advice and suggest you install it to a **subdirectory** of your $HOME dir (and then add to your PATH as necessary)

First remove the unpacked Tisean_3.0.1 source directory that you're currently using, then:

```

mkdir -p $HOME/tisean/bin

tar xvf path/to/TISEAN_3.0.1.tar.gz

cd Tisean_3.0.1

./configure --prefix=$HOME/tisean

make

make install

```

Of course you can choose whatever name you want for the directory 'tisean' under $HOME

---

### Post by Nicola_Staffolani on 2014-07-14
I followed exactly what you told me (adding minus xvf to the tar command, which, I think, you forgot) but I keep getting the same error message ;( '[FONT=courier new]make: *** [do_install] Error 1[/FONT]'; I have tried to look for the string "Error 1" in the files inside Tisean_3.0.1, but I could not find any... Could it be that my problem is that, when configuring, I get the following warning: 

[FONT=courier new]checking whether (f77  ) works... no
checking whether (g77  ) works... no
checking whether (f77 +U77  ) works... no
checking whether (f77 -q -f -B108 -lU77  ) works... no
configure: warning: 
*** No usable Fortran compiler found
*** You will not be able to use some of the routines
*** If you do have a working Fortran compiler called, say, myf77 -trick, do:
***    $ setenv FC myf77 -trick
*** and rerun
[/FONT]
Or might it be that I have a problem with make? I had a look in my software center and make is installed...

---

### Post by steeldriver on 2014-07-14
Yes - clearly if there is no Fortran compiler, then the 'make' stage will fail, and there will be nothing to 'install'. You will need to install a Fortran compiler e.g.

```

sudo apt-get install gfortran

```

and then start over. If you don't have sudo privileges you will need to ask your system administrator to do that for you.

---

### Post by Nicola_Staffolani on 2014-07-14
Wonderfull steeldriver, that was the problem!! Actually I have installed gfortran as you told me, 

> **steeldriver said:**
> 
```

sudo apt-get install gfortran

```


but I've got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gfortran is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

And indeed, as I already had told, the fortran 95 was already installed on my computer. But then I thought I might need another version of fortran compiler, so I googled "how to install a fortran compiler ubuntu" and then installed the fortran 77 compiler and now tisean is workinmg, so that was the problem!! 

Hearthly thank you very much steeldriver, I don't think I would have been successfull without your help!!!!!!!!!!!!   :lolflag:

---

### Post by Nicola_Staffolani on 2014-07-14
PS should I declare this problem as solved or will some administrator/moderator of the forum do it?

---

### Post by steeldriver on 2014-07-14
You should mark it as SOLVED yourself using the 'Thread Tools' drop down menu near the top of the page

In future, you should ALWAYS note and correct errors from the ./configure stage before moving on to the 'make' (and likewise, fix any errors from 'make' before trying to 'make install')

---

### Post by Nicola_Staffolani on 2014-07-14
OK, thank you again for your precious advices!!! 
Nicola

---

### Post by bahaaqm on 2015-03-02
Hi mate,
I think the problem is regarding to install fortran compiler (checkyour warning message).
you can install fortran compiler or just fortran 
sudo ap-get install fort77


Regards

Bahaa

---

