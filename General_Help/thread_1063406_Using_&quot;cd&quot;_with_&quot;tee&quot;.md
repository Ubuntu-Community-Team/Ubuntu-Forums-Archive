---
title: "Using &quot;cd&quot; with &quot;tee&quot;?"
date: 2009-02-07
forum: General Help
---

### Post by computer_freak_8 on 2009-02-07
Firstly, I'd like to note that I'm not sure if I am posting in the proper section. Please move this if it's improperly placed.

I can't seem to be able to use "cd" with "tee". I can't change the directory; it is as if I just hit [Enter] without typing in anything. (Nothing appears in the output file, either.)
Example:
```
jaredtbrees@multiboot:~$ cd .. | tee -a /home/jaredtbrees/Desktop/out.out
jaredtbrees@multiboot:~$ 
```

Why is this? How can I fix it?

---

### Post by yeats on 2009-02-07
cd doesn't create any output (that I can think of) - what are you trying to do accomplish?

---

### Post by kayvortex on 2009-02-07
Well, cd *will* output if there's an error (like the directory to change to doesn't exist).

The reason why cd doesn't seem to do anything is that when piping command1 to command2, the shell will run command1 in a child process and then pass the output to command2 to run. So, if you use cd in a pipe, you will cd in the child process only and it will not affect your parent environment. For example, try running:
```
( cd / && ls ) | tee ~/test.out
```
This *will* list the files in / ; so, you can see that cd is working, just not the way you expect it to.

---

### Post by computer_freak_8 on 2009-02-07
Thank you both for your responses.

Ahh, okay. I have created a keylogger-type script for my ~/.bashrc on another machine, and I can't change directories.

I guess I'll have to write an exception into it - shouldn't be too hard.


My question now is: are there any other commands that I should add an exception for? (Any other commands that normally produce no output?)

---

### Post by kayvortex on 2009-02-07
Well, I'm not sure I understand your question. Generally, any command that doesn't need to tell the user anything will normally not produce output, unless specifically told to do so with the "--verbose" flag (like cp, mv, rm etc.). But without any specifics on how you're trying to do what it is you're trying to do exactly, then there's not much else I can say really.

---

### Post by computer_freak_8 on 2009-02-08
> **kayvortex said:**
> Well, I'm not sure I understand your question. Generally, any command that doesn't need to tell the user anything will normally not produce output, unless specifically told to do so with the "--verbose" flag (like cp, mv, rm etc.). But without any specifics on how you're trying to do what it is you're trying to do exactly, then there's not much else I can say really.
Yes! There we go! You were off to a good start. As I mentioned above I added a section to my "~/.bashrc" file on another machine, but I am unable to change directories. Therefore, I will need to add an exception for "cd", so that it does not go through the "tee" command.

So, we have cp, rm, mv, cd, touch, chgrp, chmod, chown, bzip2, bunzip2, gzip, gunzip, mount, umount, .... Am I missing any? (Or, do any of these normally produce output, and I'm just not thinking of it?)

---

### Post by kayvortex on 2009-02-08
None of them produce output (but beware of shell aliases); and, off the top of my head, you might also want to include mkdir and rmdir. **But**, from what I think you're trying to do, why not simply add all the commands you want to add to ~/.bashrc in another file instead, say ~/.bashrc_custom, and then add:
> [ -r ~/.bashrc_custom ] && source ~/.bashrc_custom | tee ~/bashrc.log || echo "Error: ~/.bashrc_custom not sourced!" >> ~/bashrc.log
to ~/.bashrc? This basically says to check whether ~/.bashrc_custom exists and is readable, and if so source it and tee the output to ~/bashrc.log, or else put an error message in ~/bashrc.log. This way, all your commands get run, and you don't have to worry about piping all your commands individually. Note that, again, any cd's will not affect the terminal running ~/.bashrc, so if you want a change of directory at the end of it all, just add this to ~/.bashrc instead:
> [ -r ~/.bashrc_custom ] && source ~/.bashrc_custom | tee ~/bashrc.log || echo "Error: ~/.bashrc_custom not sourced!" >> ~/bashrc.log
cd "/dir/to/change/to"

---

### Post by computer_freak_8 on 2009-02-08
> **kayvortex said:**
> None of them produce output (but beware of shell aliases); and, off the top of my head, you might also want to include mkdir and rmdir. **But**, from what I think you're trying to do, why not simply add all the commands you want to add to ~/.bashrc in another file instead, say ~/.bashrc_custom, and then add:

to ~/.bashrc? [...] This way, all your commands get run, and you don't have to worry about piping all your commands individually.

mkdir and rmdir! I forgot about those!

The thing is, the commands will by default be piped, given what I have in my ~/.bashrc, therefore, I will add in code that will tell it to **not** pipe the "no output commands".

---

### Post by computer_freak_8 on 2009-02-08
> **computer_freak_8 said:**
> I will add in code that will tell it to **not** pipe the "no output commands".

Actually, I won't. I just figured out a much easier way, one that does not use "tee".
```
$COMMAND &> /home/username/output.temp && cat /home/username/output.temp >> /home/username/output.out
```

---

### Post by kayvortex on 2009-02-08
> The thing is, the commands will by default be piped, given what I have in my ~/.bashrc, therefore, I will add in code that will tell it to not pipe the "no output commands".

Fair enough; although, for most programs, there's no real harm in piping output even if they normally don't ever produce output. The problem you had was because you need to be aware of programs that *only* affect your *local shell environment*. As you saw, cd is a problem because it only changes what directory your shell is active on: cd has no real value to the OS, it's only useful to the shell -- take a look, there's no cd executable on your system (in /bin or /usr/bin or anywhere). Another thing that only affects your shell environment are shell variables; so:
```
PATH=/usr/bin:/bin | tee ~/log
```
also doesn't seem to change PATH. This is because shell variables (obviously!) only affect your local shell environment. Other programs, like rm or mv etc., *do* do something independent of the shell, and so are not affected by piping.
The shell commands that *could* cause problems with piping are called builtins, and you can see all of them by typing
```
man builtins
```
and most of them could cause potentially cause problems when piping, but often in only really contrived situations.
Anyway, I hope I helped a bit.

---

### Post by kayvortex on 2009-02-08
Hang on, I might be being dense here, but isn't
> COMMAND &> /home/username/output.temp && cat /home/username/output.temp >> /home/username/output.out
just going to redirect COMMAND's output to output.temp, and then copy it over to output.out? You won't spit anything out to the screen.

---

### Post by computer_freak_8 on 2009-02-08
> **kayvortex said:**
> Hang on, I might be being dense here, but isn't

just going to redirect COMMAND's output to output.temp, and then copy it over to output.out? You won't spit anything out to the screen.
Yes, I just now noticed that... Here's the new code:
```
$COMMAND &> /home/username/output.temp && cat /home/username/output.temp >> /home/username/output.out** && cat /home/username/output.temp**
```
Now, the only problem with this is that it will wait until the command has finished before it gives any output. This might not be good for when compiling programs. Any ideas on how to fork it, or something similar?

---

### Post by kayvortex on 2009-02-08
Well, you could use '&' to send the program to the background, **but** you don't want to fork it because if a subsequent command gets run before the first one completes, the whole thing will fail. E.g.
> cat /home/username/output.temp
will fail if it is run before
> COMMAND &> /home/username/output.temp
finishes creating output.temp.

Maybe I'm just being dense again, but why bother with all this redirection and cat calls? What benefit does that bring over tee? tee is there to provide a way to do this, because using other commands like you've done create other problems.

---

### Post by computer_freak_8 on 2009-02-08
> **kayvortex said:**
> Maybe I'm just being dense again, but why bother with all this redirection and cat calls? What benefit does that bring over tee? tee is there to provide a way to do this, because using other commands like you've done create other problems.

Because "tee" will not work universally. I added code to my "~/.bashrc" file that piped every command through "tee", but I could not use certain commands (for example, "cd"). Therefore, it was either make a list of all commands that, by default, do not produce output, and then code in exceptions to the "tee"ing for those specific commands, OR, I could just do as I have done above.

---

### Post by kayvortex on 2009-02-08
Riiiiight, ok, I see! Hmmm, well, if you've constructed your .bashrc file like that, then I think you're stuck with that ugly workaround! But, having thought about it, you could still cut out the whole of the contents of your .bashrc file and put it in another file that you could source in .bashrc and redirect with tee. It depends on what exactly you've done in your .bashrc file I suppose; but if you say you can't do that, then I'm all out of ideas. At least you've got *a* working, if ugly, solution!

---

### Post by computer_freak_8 on 2009-02-08
Yeah, thanks for your help, though! I'll try to pull a copy off of that computer sometime; it would probably make more sense that way. (That is, you would be able to "see" what I've been talking about.)

Don't know how long that'll be, though. The USB ports apparently don't work, and it's a really slow machine (350MHz). I'll get it posted sometime, though.

Thanks again. (I'd use the "thank" button, but as we all know, that feature is gone for now...)

---

### Post by kayvortex on 2009-02-08
Don't mention it and don't worry about it! If you do have any more questions I'll be happy to (try to) help.

---

