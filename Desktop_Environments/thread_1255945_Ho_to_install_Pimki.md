---
title: "Ho to install Pimki?"
date: 2009-09-02
forum: Desktop Environments
---

### Post by raminaghrobis on 2009-09-02
Hi all, I'm trying to install a notepad software called Pimki ([http://pimki.rubyforge.org/);](http://pimki.rubyforge.org/);) I've managed to get it working except for the mind map feature. The website says that for this, the bin directory must be on the system path; what does that mean?

Any help welcome, thanks.

---

### Post by stumbleUpon on 2009-09-02
If you have already installed graphviz, locate the directory where it is installed.

Then open a terminal open your .bashrc file (found in your home directory) in a text editor, and add the following line

```
 export PATH=$PATH:/path/to/graphviz/;
```

where /path/to/graphviz/ is the actual location of the graphviz software on your machine. (Note if there is a 'bin' directory in the graphviz folder, append that to the above command to make it /path/to/graphviz/bin)

then do
```
source .bashrc
```

---

### Post by raminaghrobis on 2009-09-02
Thanks for the reply! 
Just one questions, the last code is for the terminal (not the .bashrc file) right?

---

### Post by stumbleUpon on 2009-09-02
yes... the last code goes in the terminal

---

### Post by raminaghrobis on 2009-09-03
I tried installing pimki it on another computer and it doesn't work. I got a warning message saying "you don't have /home/myusername/.gem/ruby/1.9.0/bin in your path, gem executables won't run". Is this the problem? If it isn't what is?

I'm rather puzzled...

---

### Post by stumbleUpon on 2009-09-03
Try appending that to your path as well

```
 export PATH=$PATH:/path/to/graphviz/:/home/myusername/.gem/ruby/1.9.0/bin; 
```

---

### Post by raminaghrobis on 2009-09-04
Well I tried what you suggested and it still doesn't work. With pimki 2.0 it just doesn't do anything, and with 1.8 I get: "Failed to execute file "pimki.rb". Failed to execute child process "/home/myusername/pimki-1.8.200/pimki.rb" (No such file or directory)."

---

### Post by stumbleUpon on 2009-09-04
i dont know what u r doing, but the file "/home/myusername/pimki-1.8.200/pimki.rb" does not seem to exist as is evident from the error.

---

