---
title: "Weird Error in Terminal.."
date: 2009-02-10
forum: General Help
---

### Post by Awesom on 2009-02-10
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

Well... I was getting somewhere and had installed the restricted-extras and was installing java and it came up with something like "you already have a version of java do you want to use that one or this one type d to see the differences between them..." so I did that and it made no sense to me the differences so decided I would just install the one they had but I couldn't go back to the other screen in terminal I tried pressing heaps of stuff didn't work.. so I closed terminal then opened it and tried to do the dkpg get-apt install restricted-extras again and tried some other codes to install java and the get-apt update one now all I get is this error :S All help appreciated.

---

### Post by x33a on 2009-02-10
type sudo dpkg --configure -a into a terminal and see if the error goes away.

---

### Post by SeanTater on 2009-02-10
This should probably solve your problem
```
sudo apt-get -f install
```

Though if that doesn't work, try the solution it suggested:```
dpkg --configure -a
```

"Couldn't go back to the other screen"?
Dpkg has a lot of interfaces: do you mean there was a blue-background dialog *in* the terminal, or a configuration dialog outside it?

In either case, it should fix, but remember not to close the terminal. Dpkg can usually go on on it's own and if it cannot, the terminal has valuable information for fixing it.

---

### Post by Awesom on 2009-02-10
Already tried the solution it sugested before posting didn't work still doesn't :( and neither does the -f install one.. I searched the forums a bit others had the same problem but doing the dpkg - -configure -a thing worked for them but it has done nothing for me.

Oh about the other screen. It had press y to install the java but I pressed d to check what version I had then it came up with that but then had 

~
~
~
~
~
END

And I couldn't get out of that so I closed terminal :S


It comes up with same error for the -f install one
And this is what comes up when I type the - -configure -a one
```
dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

---

### Post by x33a on 2009-02-10
it seems you are typing -o instead of -a, that's what the error suggests.

---

### Post by Awesom on 2009-02-10
Hmm yeh I wasn't but I must have had a typo somewhere in there cuz I just searched the forum some more and found someone saying how to copy it straight off the site and run in terminal and it worked :D thanks for all your help anyway.

---

### Post by SeanTater on 2009-02-10
x33a's right. Looks like a typo.

Also, the> ~
~
~
END
was a text editor/pager. Press q next time and it will let you out.

---

### Post by Awesom on 2009-02-10
Oh ok thanks alot handy to know lol.

---

