---
title: "Commands"
date: 2006-09-13
forum: Desktop Environments
---

### Post by atraeyu on 2006-09-13
I've just installed Ubuntu, ruby1.8 and irb1.8.
All the tutorials I'm reading refer to running ruby and irb with the shell commands (respectively): ruby, irb

However, I have to type (respectively): ruby1.8, irb

Is there a way to create aliases in my shell so that typing ruby to run ruby1.8 or irb to run irb1.8?

Thanks.

---

### Post by mitch.c on 2006-09-13
> **atraeyu said:**
> Is there a way to create aliases in my shell so that typing ruby to run ruby1.8 or irb to run irb1.8?
I think what you really want is a symlink; for example:
```
sudo ln -s /usr/bin/ruby /path/to/ruby1.8
```Although I'm surprised one doesn't exist already.

Aliases are usually used to change the behavior of a shell command like:
```
# Forces confirm on any mv
alias mv='mv -i'
```
The symlink is persistent. If you go the alias route, you'll have to add them to .bashrc (assuming bash is your shell) or source them in some other way.

---

### Post by atraeyu on 2006-09-13
That looks about right.  I think the code was supposed to be:
```

sudo ln -s /path/to/script command

```

Is there a way to list symlinks?

---

### Post by skymt on 2006-09-13
You're confusing symlinks with aliases. Two entirely different things. A symlink is (basically) a file that points to another file. An alias is a shell thing. It says "when I type x, I mean y, so translate for me".

However, in this case, you don't need to do either. Just install the *ruby* and *irb* packages, they have symlinks in them and will always pull in the default version of ruby and irb (important once 2.0 hits).

---

### Post by mitch.c on 2006-09-13
> **atraeyu said:**
> I think the code was supposed to be:
```

sudo ln -s /path/to/script command

```

Oops. I can't believe I did that.

> Is there a way to list symlinks?
Try something like this...
```
ls -la | grep ^l
```

---

### Post by atraeyu on 2006-09-13
> **skymt said:**
> You're confusing symlinks with aliases. Two entirely different things. A symlink is (basically) a file that points to another file. An alias is a shell thing. It says "when I type x, I mean y, so translate for me".

However, in this case, you don't need to do either. Just install the *ruby* and *irb* packages, they have symlinks in them and will always pull in the default version of ruby and irb (important once 2.0 hits).

Gotcha.  I actually did install the ruby1.8 and irb1.8 packages.  I can run a ruby script using the shell command ruby1.8 <filename> - however, ruby <filename> produces "bash: ruby: command not found"

Similarly, I can load up the ruby real-time interpretor with "irb1.8" but "irb" produces: "bash: irb: command not found"

Like I mentioned earlier, I installed ruby1.8, irb1.8, and rdoc1.8 - according to the ruby website, those are the only files I needed to install.  I installed them using apt-get.

So I'm pretty sure that either a) something went wrong with the installation (I don't think it did) b) I didn't install something that needed to be installed (I don't think this is the problem either) or c) I need to manually set my shell to recognize that the command "ruby" should run the most current ruby executable.

According to what you said though, it should have done this automatically ... and you said that this is important once web2.0 hits ... how come?  Is there something I've done wrong?  Something I need to fix?  Or can I just manually create these symlinks?

(On a related note, any idea where the ruby executable is?)

---

### Post by atraeyu on 2006-09-13
> **mitch.c said:**
> Oops. I can't believe I did that.


Try something like this...
```
ls -la | grep ^l
```

Ok, so a symlink is represented by a little ".filename" in my home directory.
However, if I try to more ".filename" I simply get:
*** .filename: directory ***

I can't view the contents of this?

---

### Post by skymt on 2006-09-13
You misunderstood me: I really meant to install the packages called "ruby" and "irb". No "1.8" tacked onto the end. Also, I meant Ruby 2.0, not Web 2.0. Web 2.0 already hit and ran! ;) 

When Ruby 2.0 is released, if you have the "ruby" and "irb" packages installed, it'll automatically upgrade you. If you just have "ruby1.8" and "irb1.8", it'll stay at that version.

As for symlinks, I don't think I can explain it better than [Wikipedia](http://en.wikipedia.org/wiki/Symlink). (EDIT: See especially the Similar Concepts section where it compares symlinks to Windows shortcuts and MacOS aliases

---

### Post by atraeyu on 2006-09-13
Thank you!  I really appreciate it.  Thanks for the wikipedia link, I should have just done that myself ...

Sorry, I hate to be a nag, but just to clarify - I should install the ruby and irb packages in addition to the ruby1.8 and irb1.8 packages?

---

### Post by skymt on 2006-09-13
> **atraeyu said:**
> Sorry, I hate to be a nag, but just to clarify - I should install the ruby and irb packages in addition to the ruby1.8 and irb1.8 packages?

Yep!

---

### Post by mitch.c on 2006-09-13
> **atraeyu said:**
> Ok, so a symlink is represented by a little ".filename" in my home directory.
However, if I try to more ".filename" I simply get:
*** .filename: directory ***

No. A symlink is noted in an ls -l listing by the 'l' character in the first column like this:
```
user@ubuntu:~$ ls -l /usr/bin/ruby
lrwxrwxrwx 1 root root 7 2006-08-09 02:18 /usr/bin/ruby -> ruby1.8
```
That's why ls -la | grep ^l shows the symlinks. grep only shows the results of the ls -la command where the first character is an 'l'. If you want to write the results to a file, try:
```
ls -la | grep ^l > symlinks
```
The where and which commands are useful for finding executables. For example you could have found ruby1.8 using:
```
which ruby1.8
```
A really handy combination of ls and which is something like this:
```
 ls -l `which python`
```
This will find the python command your path points to and give you the long ls listing which in turn show whether it is a symlink, or the actual executable (hard link).

---

### Post by atraeyu on 2006-09-13
Wow, thanks both of you.  
Installing ruby & irb packages did automatically update my system so that "ruby" and "irb" point to the most recently installed packages.  

And I now understand symlinks, thanks!

---

