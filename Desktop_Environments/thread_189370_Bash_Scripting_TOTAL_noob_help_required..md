---
title: "Bash Scripting TOTAL noob help required."
date: 2006-06-05
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-06-05
Ok, so I had the idea that I would like to learn to do a spot of scripting, and came up with the following idea of a script to write as a first port of call as a means of learning (though I would also like to get it up and working anyway!).
I should note that I am a total beginner in all fields of scripting, and don't know if this should be in python or bash.

This was my ideas for how the script should be laid out - however of course this is all pseudo-code.  Hopefully it should be clear what I *intend* it to do, but if not, see the explanation below.

```

On: (*Permission Denied*)          #this is supposed to activate the script when the output of a command informs you there was an error as permission was denied. I believe this would mean that it would have to run as a daemon
	echo "this action may require root access.  Do you wish to prefix sudo to the command (Yes/No/Retry)?"         #underline Y/N/R

		If answer=y
			then "sudo $TriggerCommand"         #this is supposed to redo the command you have just performed, but with the sudo command refixed

		If answer=n
			then exit            #this is supposed to just send you straight back to the input command, exiting this daemon - is this done using 'fi'
			#echo "exiting" ; fi #would this work?
			#echo 'exiting' ; \newline

		If answer=r
			then "$TriggerCommand" & $IgnoreDaemonOnNextAttempt            #this is supposed to run the original command unaltered, but not trigger this daemon - just in case this daemon would interfere with anything.  Obviously this code is far short of working.

## Notes: 
## Is there an inbuilt bash variable similar to intended purpose of '$TriggerCommand' ?
## How define variables? alias within script (alias x='y')? Or just x=y? Or some other way?


```

The script is supposed to run in the background as a daemon, and scan the outputs of commands input into the shell, and look for "permission denied" errors (or similar).  It will then ask if you want to retry the command with sudo prefixed, giving you three options (yes, no, and 'retry and ignore the error' - just in case this script interferes with anything).  Obviously it will then do what you have just told it to do!

---

### Post by judgekaster on 2006-06-05
If you really like to learn more about bash scripting, I suggest you look up the ["Advanced Bash Scripting" Tutorial]("http://www.tldp.org/LDP/abs/html/")

Let me offer the following code for starters

```

#!/bin/sh

# $UID is the numerical id of the user that invoked the script; root's UID is 0
# $0, $1 and so on pertains to the command line parameters, $0 being the script invoked
if [ $UID != "0" ]; then
   sudo $0
   echo "You're now root"
fi


```

Hope this helps.

---

### Post by Lunar_Lamp on 2006-06-05
Why /bin/sh ?  

If I read your code correctly, it does this:

It checks if you are root, and if you are not root it performs the command "sudo $0" and says "you are now root" and exits.

I don't understand the $0 variable though.  From what I can work out it would cause this script to be run again as root, which would create an infinite loop surely?

---

### Post by judgekaster on 2006-06-05
As noted in the commented line in the code snippet provided, the variable $0 is a built-in variable that pertains to the command line arguments. In the command line:

```

$ command argument1 argument2

```
$0 = "command"
$1 = "argument1"
$2 = "argument2"

The line #!/bin/sh is what is usually referred to a the "shebang" line. It tells the shell which interpreter you will use. "/bin/sh" is a symbolic link to "/bin/bash". You will see what I mean if you 

```

$ ls /bin/sh

```

The script I showed you just tells you how to determine if the script was run as root. I didn't try to write the code of your entire pseudocode. I figured you will want to do that yourself. :)

---

### Post by Lunar_Lamp on 2006-06-06
Sorry, I was aware of the purpose of the shebang line, I had hadn't realised that /bin/bash could be substituted for /bin/sh.

So, to make 100% on the script:
The variable $0 could be described as "the original command input by the user, with no added arguments"?

---

### Post by judgekaster on 2006-06-06
You can say that...

---

### Post by Lunar_Lamp on 2006-06-06
...but I'm guessing by your response that it's not technically correct, heh!  Thanks though, I shall go away and see what I can work out on the info you have given to me :-)

---

### Post by Lunar_Lamp on 2006-06-06
Ok, this is what I came up with after a few minutes of thinking:

```
#!/bin/bash

command=$0  #is this bad practice?

	if [ $output = *Permission denied* && $1 != --ignore-sudoer-helper-script ]; then  	

#don't know what $output neds to be.  
#the latter part of this is supposed to make the script skip any commands suffixed with the option --ignore-sudoer-helper-script.
#is && correct for 'and'?

		echo "This command may require root access, do you wish to retry as root? (Y/N/R)"
			{ Detect user input (called $answer)

				if [ $answer = "y" ]; then
						echo "retrying with: sudo ${command}"
						sudo $command
					fi

				elif [ $answer = "n" ]; then
						echo "exiting"
					fi
	
				elif [ $answer = "r" ]; then
						echo "retrying"
						$command --ignore-sudoer-helper-script
					fi }
	elif [ $1 = --ignore-sudoer-helper-script ]; then
		echo 'ignored sudo helper script'
			fi

```

---

### Post by judgekaster on 2006-06-06
no problem :)

---

### Post by Lunar_Lamp on 2006-06-07
No problem?  Well, I presume that means that what I wrote woul work! hehe.

But:
 - I use $output to mean the output of a previous command on screen, which I don't know how to interpret.  
 - I have no idea how to trigger this script.  I think I may need to break it into two, a daemon one to watch the output of all commands input to pick up permission denied, and another to actually perform what i've outlined above.

Perhaps, something like this:

```
if [ $output = *permission denied* ]; then
          /bin/bash/sudoer-helper-code
elif wait
```

But again:
 - this uses the magical variable $ouput
 - I don't think wait can work, as it doesn't do what I want.

I need to ```
wait until $output !=""
```, i.e. wait until there is an output - then check to see if permission denied is in there.

---

### Post by judgekaster on 2006-06-08
sorry... the "no problem" was in response to your #7 post. seems you posted ahead of me that is why mine was posted below post #8. at any rate...

at the risk of turning this forum into a bash scripting forum, let me react to some points with regard your post:

(a) i don't get where $output comes from... do you want to capture the output of a command? you can do so by:

```

OUTPUT=$(command)

```

(b) to read the response from a user, you can:

```

echo "Do you wish to retry? "
read RESPONSE
echo "Your reply: $RESPONSE"
# handle $RESPONSE here

```

That's it... I hope this helps.

---

### Post by Lunar_Lamp on 2006-06-08
a) Yes, I want to run this script in the background all the time (as a daemon), and get it to respond to the output of any command input, so that if I typed, "apt-get install foo", when it says "permission denied", this script will be activated and ask me if I want to retry with sudo access.  I don't really understand "OUTPUT=$(command)" - doesn't that just declare any instance of $OUTPUT in the script to be treated as $(command) - and I thought "command" in this script was just the initiating command, not including the output from it?  :-S

b)Thanks, I hadn't discovered the 'read' command, which was obviously what I was looking for.

---

### Post by Fafnir on 2006-06-08
Here's my take on things, speaking as a scripting and Linux newbie (but programming semi-veteran)...

[QUOTE=Lunar_Lamp]a) Yes, I want to run this script in the background all the time (as a daemon), and get it to respond to the output of any command input, so that if I typed, "apt-get install foo", when it says "permission denied", this script will be activated and ask me if I want to retry with sudo access.  I don't really understand "OUTPUT=$(command)" - doesn't that just declare any instance of $OUTPUT in the script to be treated as $(command) - and I thought "command" in this script was just the initiating command, not including the output from it?  :-S[/QUOTE]

You'd think, but OUTPUT=$(command) is different to OUTPUT=$command. It's a VERY weird choice of nomenclature, I know, but that's the way it is. Basically, OUTPUT=$command assigns the contents of $command to OUTPUT (as you already know). OUTPUT=$(command) executes the contents of $command, then pipes the output through to OUTPUT. It's very similar to OUTPUT=`$command`, if you're familiar with that notation. 

The reason we use this painfully obscure notation instead is that there used to be some insanely complicated rules regarding the use of nested backticks (e.g. OUTPUT=`$command parameter `$command2``), which no-one really liked, but backtick syntax couldn't be changed without breaking compatibility with earlier versions... :-( What it boils down to is that if you use `` notation in this script, your script will almost certainly break if it encounters `` (and possibly other things) in your commands.

Other points:

1. For the --ignorescript parameter, you wouldn't normally just check the first parameter of the command, you'd check them all to prevent potential weirdness later. You also need to take  the parameter out before running the actual command, or the command will just notice there's a parameter there it doesn't like and refuse to run. I think the easiest way of doing this would be to use the $* variable. Yes, that's really a variable name. Basically, it contains every single parameter the variable receives - here's an example to illustrate. If I run foobar as follows:

```
./foobar --discombobulate --vorpalbunny -reticulate_splines insertsillyfilename
```

then here's what all the parameter-related variables look like:

```
$0 = ./foobar
$1 = --discombobulate
$2 = --vorpalbunny
$3 = -reticulate_splines
$4 = insertsillyfilename
$* = --discombobulate --vorpalbunny -reticulate_splines insertsillyfilename
```

So in this case, you can use grep to check whether the parameter is present, then remove it with sed or something, then make the script execute $0 $* by the shell.

2. Your conditional syntax (the if [ ] parts) is pretty much OK - the only thing is that for "historical reasons" (I'm guessing), we use -a instead of &&. Also, you need quotes around variable names in if statements.

The basic reason for *that* is that what if [ ] actually does is run a program called test (which you can run separately if you want - try it!) The old syntax was 'if test expression', but it got shortened to if [ expression ]. Unfortunately, all that means is that the interpreter substitutes 'test' for '[' - hence the spacing requirements. The other problem is that if you have something like this:

```
if [ $4 == "frobnitz" ]
```

then if $4 is actually empty (i.e. there's no fourth parameter), it'll be parsed as this:

```
 if test == "frobnitz"
```

which is nonsense. And nonsense makes test unhappy. And when test is unhappy, the interpreter gets upset. And when the interpreter gets upset, SCRIPTS FAIL! (Ah, Austin Powers...) If we put quotes around the variable name, though, we come up with:

```
if test "" == "frobnitz"
```

which is telling test to check against an empty string, which it can just about handle.

3. As judgekaster says, you want read for getting input.

4. Very minor thing - there's no fi at the end of an elif until you get to the last elif. So it goes:

```
if [ something ]; then
do stuff
elif [ some other thing ]; then
do other stuff
elif [ some totally different thing -a 42 is the meaning of life ]; then
format hard drive
fi
```

so you only need one fi.

5. As for renaming $0 being bad practice... Well.. It is a *tiny* bit, and someone might make a frowny face at you if you did it in kernel code or a driver or something, but right now all that matters is you getting to grips with the language. So if having system variables named $0 and $* and god knows what else is making it harder to understand the code, then good practice - at least for now - should be thrown full force out of the window.

6. Now we come to the problem of the output, and how to make sure the script gets called when it should. This appears to be the tricky bit, and possibly the show-stopper - frankly, I have no idea.


The basic problem is that I don't ***_THINK***_ (note emphasis) a daemon will work. Please note that my knowledge about daemons basically consists of some googling, so please take the following with extreme skepticism. Basically, the way most daemons function is like this:

1. The original daemon process is started, e.g. by running from a command line (duh).

2. That process then starts (or forks) a second process that will keep running even after its parent quits.

3. That means that the parent process, the one you originally started, CAN quit, so it does, freeing up it's parent process (e.g. the terminal window you opened the daemon with). So now the daemon is running in the background.

4. The daemon enters The Big Loop. Basically, it looks something like this (shamelessly stolen from [a more advanced link]("http://www.linuxprofilm.com/articles/linux-daemon-howto.html#s5")):

```
while (1) {
     /* Do some task here ... */
     sleep(30); /* wait 30 seconds */
}
```

It has to wait a few seconds between executions so it doesn't use too much CPU time. So if you want the daemon to run a script every time you use a command, you have to either wait ten seconds for it to kick in, use up a huge amount of CPU time, or find a way of 'waking' the daemon whenever a command is used. I don't know of one, but then I know very little about daemons.

The other problem with daemons is that you have to write them in a lower-level langauge than shell scripting - something like Perl or C - and they're often really nasty to debug if something goes wrong.  Not a fault with daemons in themselves, but since you're using this to learn shell scripting, it's hardly ideal in this case!

It's possible there's some equivalent in shell scripting, but I haven't found it so far. Closest I've come is the 'alias' command, which lets you substitute any command for a second string - e.g.

```
alias ls 'ls -l'
```

The problem is, it doesn't accept wildcards! Otherwise you could alias every command to a program that examined its output, then called the script to prompt for a sudo if it contained "Permission denied"... So, I'm clueless on this one - sorry.

The other thing you might look at is exit codes - it's possible that any command that fails due to lack of permissions may return a constant value (every command returns a value upon execution) - in which case, checking that value would be a good way to check whether the command had failed. You still come up against the problem of how to check the value, though...

I think this is a case of rather serious bad luck on your part, in that you took on such a nasty project! The important thing is *not to let this dishearten you*. There are lots of interesting and useful things you can do with scripting - daemons just aren't among them... :-( It's a very interesting problem, though - I'll have a go at it myself in C, see whether I can get something working...

There is a *sort* of (non-scripting) substitute you could use, though, although it's imperfect and somewhat irritating. In an xterm window, you can use the up and down cursor keys to cycle through the command history. So when you get the permission denied message, you can just type [UP] [HOME] "sudo " [ENTER].

Good god, that was a long post... I should really be revising...

---

### Post by judgekaster on 2006-06-08
that's quite a handful of insights. 

i've been playing with bash for 2 years now, to do some administrative tasks. and as always, one learns new things how to do things...

---

### Post by Lunar_Lamp on 2006-06-08
> ...you can just type [UP] [HOME] "sudo " [ENTER]....

It was precisely because that was so easy I thought it would try and make a script to do it for me.

I should point out that I have no experience of scripting nor programming in *any* language.  I chose bash because it's the one I figured would be most useful to me as it would enable me to learn more about linux at the same time as learning some coding discipline.  Anything I guessed correctly comes purely from what I've observed in other code to which I have been exposed (albeit in an non-understanding way).  So, the whole part about backticks is a bit over my head, but I understand what you meant in a general sense.

Now you say it, it's actually almost obvious that $* would do what you said, heh.  I have no idea what sed is - but a little bit of googling has given me a vague idea what it is you mean.  My one concern (read unresolved flaw in my understanding) is that $* would be 'all variables declared in the script and known by bash' - however I presume that when you refer to it after $0 it becomes almost a subset of $0 - i.e. "$0 $*" means, 'any variable whatsoever that is preceded by $0"?

On a different tack, I was writing the script in gedit; which was nice, particularly with the syntax highlighting making it pretty, even if I didn't quite understand all of it.  However, I have no way of testing the scripts other than creating a new bash script to run, however I am sure tehre much be some kind of automated bug highlighter out there.

Oh, and THANKYOU Fafnir for your post (and you also judgekaster!).

---

### Post by Fafnir on 2006-06-08
> **Lunar_Lamp]It was precisely because that was so easy I thought it would try and make a script to do it for me.[/QUOTE]

Always the way of it... Sorry if I insulted you by pointing that out, it's just that I myself have a habit of taking every problem as a chance to learn about the internals of Linux, failing,  then finding there's a nice friendly button somewhere to do it all for me!

[QUOTE=Lunar_Lamp]I should point out that I have no experience of scripting nor programming in *any* language.  I chose bash because it's the one I figured would be most useful to me as it would enable me to learn more about linux at the same time as learning some coding discipline.  Anything I guessed correctly comes purely from what I've observed in other code to which I have been exposed (albeit in an non-understanding way).  So, the whole part about backticks is a bit over my head, but I understand what you meant in a general sense.[/QUOTE]

Good choice with bash - it's got a few inconsistencies, but it also has high-level features for a lot of stuff that can get irritating in other languages (e.g. text manipulation). When you start looking at branching out into other languages, Python might be a good next step. It's basically a simple, powerful scripting language for when shell scripts won't work for one reason or another.

The backticks come from shell scripting - I just mentioned them because I see them a lot more often than the $() notation, so I thought you might have come across them in your travels. If you haven't seen them before, just take it as a piece of history!

[QUOTE=Lunar_Lamp]Now you say it, it's actually almost obvious that $* would do what you said, heh.  I have no idea what sed is - but a little bit of googling has given me a vague idea what it is you mean.  My one concern (read unresolved flaw in my understanding) is that $* would be 'all variables declared in the script and known by bash' - however I presume that when you refer to it after $0 it becomes almost a subset of $0 - i.e. "$0 $*" means, 'any variable whatsoever that is preceded by $0"?[/QUOTE]

This is one of those little inconsistencies... Basically, * only seems to be interpreted as a wildcard when it's a standalone character or the command you're using is specifically set up to use * as a wildcard. Now, most commands (including just about every search command, navigation command and file manipulation command) *are* set up to use * as a wildcard, so for example

```
cp *.gif /home/foobar/images
```

works, even though * is part of a larger string. But if you open up an xterm try something like this for yourself:

```
echo *
echo *foobar
```

then you'll see it doesn't work that way for everything. Wildcards don't work with variable names, so $* simply means "a variable named '*'", rather than "all variables" or worse, "a variable named after every single file in the current directory". As to *why* this slightly... quirky... name was used, I would guess the thought process went along the lines of:

"Well, everyone knows * means "all", so this makes sense for the variable name for all parameters."

So, in other words, $* is just a variable like any other - despite the strange name. So eg "echo $0 $*" just means "print the contents of the variable named 0, then the contents of the variable named *" - which would be everything typed to invoke the script.

[QUOTE=Lunar_Lamp]On a different tack, I was writing the script in gedit said:**
> 

Wait - gedit has syntax highlighting now? *checkcheckcheck* So it does! Thanks - I never even noticed that! :oops: You can probably take it from that that I don't know any more advanced tools - sorry. I'd be interested if anyone else had anything, though.

[QUOTE=Lunar_Lamp]Oh, and THANKYOU Fafnir for your post (and you also judgekaster!).

And thank YOU for pointing out the highlighting in gedit - that'll come in handy a lot! :-)

---

### Post by adam s on 2006-06-08
Hi,

I found this post while seeing if I could find out why my shell scripts aren't running.

There is a bourne shell command called **trap** that may help create your daemon. This may be what you are looking for - it normally works when the kill command is run.

For more info look in sources like the O'Reilly UNIX power tools book or on the web.

I have never used this command so do not have any detailed knowledge about it.

Adam

---

### Post by thasheep on 2006-06-08
I don't know how one would write such a daemon, but according to /usr/include/sysexits.h, the exit code for 'permission denied' is 77. This could be useful. Perhaps monitoring stderr somehow....

---

### Post by Lunar_Lamp on 2006-06-08
Yes, that is indeed useful.

So, stderr is a file that contains error codes etc - so I run the script whenever that file is accessed, and check for NEW instances of exit code 77, and if it;s tehre run the script, if not go back to sleep.

Is that a good general purpose idea?

---

