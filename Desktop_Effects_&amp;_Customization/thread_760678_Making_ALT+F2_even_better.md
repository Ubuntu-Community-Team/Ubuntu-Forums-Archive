---
title: "Making ALT+F2 even better"
date: 2008-04-20
forum: Desktop Effects &amp; Customization
---

### Post by StooJ on 2008-04-20
I love the run application dialogue box. I'm lazy, and sometimes I cannot be bothered moving my hands off the keyboard and onto the mouse to open a programme. ALT+F2, then type the name of the programme and it's up and running.

I open the terminal, amarok, pidgin, a calculator, tomboy... the list goes on and on.

However, if I want to run the calculator and am in autopilot, I ALT+F2 and type Calculator. The calculator comes up as one of choices in the "Show list of known applications" box below, and it is highlighted, but if I press the return key I get an error saying "Could not open location 'file:///Calculator'"

What it is really looking for me to type is "gcalctool"

The same happens with Terminal. It's looking for "gnome-terminal", although "Terminal" will display the programme in the list below

Now, I realise that I could assign different keyboard shortcuts to run these programmes individually, but I really like being able to type a word and get the right programme.

What I'd really love is someway to create an alias or something so that typing "Terminal" will run "gnome-terminal", or calculator running gcalctool.

I tried creating a bash script and adding the path to my .bashrc, but I still get an error saying it couldn't open the file.

So, how can I do this? I'm sure it can be done.

Many thanks

---

### Post by FuturePilot on 2008-04-20
You can create something called a bash alias. You really shouldn't add aliases directly to your ~/.bashrc. Instead create a file called .bash_aliases (note the . dot in front of the name) and put them in there.
For example
```
alias Calculator='gcalctool'
alias Terminal='gnome-terminal'
```
etc.
Then open the .bashrc file and uncomment these lines

```
#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi
```
by removing the # signs and saving it. Logout then log back in. Calculator should open gcalctool and Terminal should open gnome-terminal now.

Aliases are fun :D

---

### Post by diaa on 2008-04-20
Are you using full path when setting up the alias?
may be you can create simple one-line bash scripts and put them in ~/bin

for example create the file calculator to run gcalctool, the contents of the file should be as follows
```
#!/bin/sh

/usr/bin/gcalctool
```

then just make the file executable
```
chmod a+x calculator
```

and place it into ~/bin and you'll be able to run it from anywhere.

generally I suggest [gmrun]("http://www.bazon.net/mishoo/gmrun.epl") as a better alternative to gnome's run dialog.

---

### Post by StooJ on 2008-04-20
Thanks for the replies.

Making an alias works great for inside the terminal (glad I know how to make them now)

Unfortunately, it doesn't work in Run Application. Any other ideas?

I don't seem to have a bin folder in my home dir, I will try making it and adding it to my $PATH, then trying the script from there.

---Edit---

Nope, doesn't work either.

Is my only option gmrun?

---

### Post by diaa on 2008-04-20
> **StooJ said:**
> Thanks for the replies.

Making an alias works great for inside the terminal (glad I know how to make them now)

Unfortunately, it doesn't work in Run Application. Any other ideas?

I don't seem to have a bin folder in my home dir, I will try making it and adding it to my $PATH, then trying the script from there.

---Edit---

Nope, doesn't work either.

Is my only option gmrun?

That's strange, the method I mentioned works fine for me from both gmrun and gnome's run dialog.

also ~/bin is already added to PATH for me without any manual changes.

*PS:For some reason some applications don't work if they're not run from the terminal, [wikidpad]("http://www.jhorman.org/wikidPad/") for example, but not gcalctool*

---

