---
title: "Bash command history search"
date: 2009-04-09
forum: General Help
---

### Post by ashwinhgtx on 2009-04-09
Is it possible for me to search through the history of all my previously used commands instead of pressing the up key many times to find a previously used command?
I'm sort of a newbie when it comes to the terminal and I find it easy to learn and practice commands by using them again and again. So when I get a syntax error all I need to do is do an instant search to find the last time I used the command properly. I know the man pages will explain that but I find it's faster if I get my own command with my specific arguments and paths.
Also is it possible to set a limit to the number of commands saved in the command history?

---

### Post by taurus on 2009-04-09
Look in ~/.bash_history.

```
more ~/.bash_history
```

---

### Post by ashwinhgtx on 2009-04-10
> **taurus said:**
> Look in ~/.bash_history.

```
more ~/.bash_history
```

Thanks for that.
I am able to view the list of all the commands in the history. How can I search through it? And how do I set the number commands to be saved in the command history?

---

### Post by FrankT-Qc on 2009-04-10
There's a command called history (eheh) that does pretty much everything you need to do.

start with ```
man history
```

---

### Post by ashwinhgtx on 2009-04-10
> **FrankT-Qc said:**
> There's a command called history (eheh) that does pretty much everything you need to do.

start with ```
man history
```

I will check it out soon. The man page is huge.

---

### Post by bodhi.zazen on 2009-04-10
In a terminal, hit Ctrl-R for recusive search

start typing fragemnts of a command

you will see the most recent match

To cycle through matches, keep hitting Ctrl-r

to select a match hit the enter key

---

### Post by ashwinhgtx on 2009-04-10
> **bodhi.zazen said:**
> In a terminal, hit Ctrl-R for recusive search

start typing fragemnts of a command

you will see the most recent match

To cycle through matches, keep hitting Ctrl-r

to select a match hit the enter key

Thanks a lot. I got what I wanted.

For anyone who is interested, I also found this: [http://www.tuxradar.com/content/more-linux-tips-every-geek-should-know](http://www.tuxradar.com/content/more-linux-tips-every-geek-should-know)

This is the concerned extract:

[I]'#12: Re-using old commands.

It's a pretty common situation to find you once typed a huge long command that you thought you would never need again, but now you do, but what's the fix? Well, if you're using Bash, you can make use of the history feature (use the Up arrow) of Bash. But what if you have only a vague memory of the command? The history command can help:
history | grep -i "<yoursearchstring>"

The numbers indicate the history file number of the command, you can execute it by simply typing '!' followed by the number at the bash prompt.'[/I]


Thanks a lot everyone. :p

---

