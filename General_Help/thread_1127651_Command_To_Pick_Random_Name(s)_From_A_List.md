---
title: "Command To Pick Random Name(s) From A List"
date: 2009-04-16
forum: General Help
---

### Post by Rytron on 2009-04-16
Hi.
I'd like a command that would take a list of names and be able to randomly pick a name or x amount of names and output the chosen names to a text file titled 'chosen' to the Desktop.
Anyone know how to do this?
Thank you.

---

### Post by codeseer on 2009-04-16
> **Rytron said:**
> Hi.
I'd like a command that would take a list of names and be able to randomly pick a name or x amount of names and output the chosen names to a text file titled 'chosen' to the Desktop.
Anyone know how to do this?
Thank you.

Man, you should look into learning a programming language with all the wild stuff you're doing. I'll look around for a solution.

---

### Post by amauk on 2009-04-16
assuming each entry on new line

```
cat /some/file | sort -R | head -1 > ~/Desktop/chosen
```

*edit*
change "head -1" to any number of choices
head -10 will pick 10 random entries

---

### Post by codeseer on 2009-04-16
> **amauk said:**
> assuming each entry on new line

```
cat /some/file | sort -R | head -1 > ~/Desktop/chosen
```

*edit*
change "head -1" to any number of choices
head -10 will pick 10 random entries

That's slick. Now is that pseudo?

---

### Post by amauk on 2009-04-16
> **codeseer said:**
> That's slick. Now is that pseudo?as in pseudo-random?
Yeah, it's not like we're doing encryption or anything :P

---

### Post by rhcm123 on 2009-04-16
> **amauk said:**
> assuming each entry on new line
```
cat /some/file | sort -R | head -1 > ~/Desktop/chosen
```


If you would like to make this command much shorter so you don't have to keep retyping it (this could get really annonying if you do this frequently), make a BASH command alias! (you could also make it a script and stash it in /bin, repost in this thread if you would like that option instead).

To make a command alias:
```
cd && nano ./.bashrc
```
.bashrc is the configuration file for bash. (Pretty chill, if i say so myself.) After the file opens, add this line here at the bottom:
```
alias ALIAS-TITLE-CHANGE-THIS-TO-YOURS="cat /some/file | sort -R | head -1 > ~/Desktop/chosen"
```

You can also use bashrc to make your terminal different colors. For iinstance, i have the line: 
```
export PS1="\[$(tput setaf 2)\]\u@\h:\w$ \[$(tput sgr0)\]"
```
in my file, which makes my terminal green. Ignore the included-script options in the file, they make it too complex. 

Read this guide [here]("http://www.cyberciti.biz/faq/bash-shell-change-the-color-of-my-shell-prompt-under-linux-or-unix/") for a list of the color codes (scroll down to the bottom). Also, the commands they give you towards the top don't work too well- i prefer the tput command because it's implemented in almost all linux distros.

Enjoy :)

---

### Post by Rytron on 2009-04-17
Thank you amauk. Perfect! ;)

Also, thanks go to you rhcm123.

---

### Post by rhcm123 on 2009-04-17
> **Rytron said:**
> Thank you amauk. Perfect! ;)

Also, thanks go to you rhcm123.

no problems

---

### Post by Rytron on 2009-04-19
This would be great as an added bonus:

A command that would take a list of names and be able to randomly **extract** 2 names from the list and output the chosen names to a text file titled 'chosen1' to the Desktop.

Until the main list is empty, there would be files output with these titles:
chosen1, chosen2, chosen3, chosen4, etc.

Anyone know how to do this?
Thank you.

---

### Post by Rytron on 2009-04-19
I have this line of code but it does not take away the chosen names from the original file.

```
cat /some/file | sort -R | head -1 > ~/Desktop/chosen
```

#change "head -1" to any number of choices
#head -10 will pick 10 random entries

---

### Post by amauk on 2009-04-19
Bash script

```
#! /bin/bash

## Variables
SELECT_FILE="/home/tony/Desktop/choices"
CHOSEN_FILE="/home/tony/Desktop/chosen"
NUMBER_CHOSEN=3

## START
CHOICES=`cat "$SELECT_FILE"`
#echo "$CHOICES"
CHOSEN=`echo "$CHOICES" | sort -R | sed ${NUMBER_CHOSEN}q`
echo "$CHOSEN" > "$CHOSEN_FILE"
echo "$CHOICES" | grep -v "^$CHOSEN$" > "$SELECT_FILE"
```

---

### Post by Rytron on 2009-04-20
> **amauk said:**
> Bash script

```
#! /bin/bash

## Variables
SELECT_FILE="/home/tony/Desktop/choices"
CHOSEN_FILE="/home/tony/Desktop/chosen"
NUMBER_CHOSEN=3

## START
CHOICES=`cat "$SELECT_FILE"`
#echo "$CHOICES"
CHOSEN=`echo "$CHOICES" | sort -R | sed ${NUMBER_CHOSEN}q`
echo "$CHOSEN" > "$CHOSEN_FILE"
echo "$CHOICES" | grep -v "^$CHOSEN$" > "$SELECT_FILE"
```


Thank you amauk. Exactly what I needed.

---

### Post by pi3r9 on 2009-05-20
the original command from above but put into a bash script and changed just a little, basically now it will generate the chosen file on the desktop but also display the result in the terminal window. also asks for the file you would like it to be generated from. maybe someone will have some use for it. 
#!/bin/bash
echo -n "$user what do you want randomly selected ? :"
read -e selected
echo
cat $selected | sort -R | head -1 > ~/Desktop/chosen && cat Desktop/chosen

---

### Post by TideMan on 2009-05-20
This is a very helpful thread in increasing my knowledge of scripting.  But I cannot find what the -R in sort does.  man sort has nothing about -R.
For me, this raises two questions:
1. What does sort -R do?
2. If one cannot find an option under man, where should one look?

---

### Post by amauk on 2009-05-20
> **TideMan said:**
> This is a very helpful thread in increasing my knowledge of scripting.  But I cannot find what the -R in sort does.  man sort has nothing about -R.
For me, this raises two questions:
1. What does sort -R do?
2. If one cannot find an option under man, where should one look?
-R randomly sorts the input

it's there in the man page

in the man viewer, use a forward slash to search
```
man sort
```then```
/-R
```

*edit*
just for completeness
man uses less as it's viewer
so '/' searches in less
'n' cycles through the search occurrences
'N' cycles though occurrences backwards

see the man page for less for all the interactive things
under the 'commands' section

---

### Post by TideMan on 2009-05-20
> **amauk said:**
> -R randomly sorts the input

it's there in the man page



Yes, I see it now.  Must be going blind..............
Or old-timers' disease ;)

---

