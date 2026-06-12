---
title: "Impossible to input latin characters &quot;a&quot; and &quot;o&quot; with macrons using Compose key"
date: 2010-08-31
forum: Desktop Environments
---

### Post by anagor_lv on 2010-08-31
This post is a little bit long. In this post I am explaining how I solved my problem.

The problem is, some compose key sequences in Ubuntu do not work correctly. For instance, <Compose key + minus + latin capital A or latin capital O> result in A and O with tildes ("Ã", "Õ"), where the majority of users would expect macrons. ("&#256;", "&#332;")

The issue has been filed as a bug report and is being worked on. Here is a link to the bug report:
[https://bugs.launchpad.net/ubuntu/+source/libx11/+bug/408651](https://bugs.launchpad.net/ubuntu/+source/libx11/+bug/408651)

This post is for those who do not wish to wait until a fix is released and prefer to make a quick fix for personal use. It requires you to define your own compose key sequences. Below I am explaining how I did it.

If you would like to learn how to activate and use a Compose key, refer to my earlier thread:
[http://ubuntuforums.org/showthread.php?t=1380581](http://ubuntuforums.org/showthread.php?t=1380581)

Here is my solution:

First, set up the appropriate input method.

Open the terminal and run the command:

```
im-switch -c
```You will get something like this:

```
anatoly@NLANGo:~$ im-switch -c

There are 8 candidates which provide IM for /home/anatoly/.xinput.d/ru_RU:

  Selection    Alternative
  -----------------------------------------------
      1        default
      2        default-xim
      3        ibus
      4        none
      5        scim
*     6        scim-bridge
      7        scim-immodule
      8        th-xim
System wide default for ru_RU (or all_ALL) locale is marked with [+].
Press enter to keep the current selection
[*], or type selection number: 2
```Your selected input method should be default-xim. If the selection is different, change it!


Now log out and log in again

After this is done, try out the compose key sequences you need to use (or example, <Compose> <comma> <k>). Do they work properly? Maybe, some compose characters won't work. For example, when you press <Compose> <minus> <a>, the result is no symbol (while you would expect "&#257;").

If any of the sequences you need work incorrectly, you are going to adjust them. This is how to do it: 

In the Ubuntu system, compose key sequences are stored in the file /usr/share/X11/locale/en_US.UTF-8/Compose
In this file, each compose sequence is defined in one line, which looks something like this:

```
<Multi_key> <macron> <A>             : "&#256;"   U0100 # LATIN CAPITAL LETTER A WITH MACRON
```(According to the syntax of this file, <Multi_key> means the compose key)
I do not know what is the <macron> key on the keyboard. It is not the hyphen (-), the hyphen is denoted as <minus>. Preferably, to enter characters with macrons, (&#257;, &#333;, &#363;, &#299;, &#275;) I want to press the Compose key, the hyphen (dash), and the letter. So, the desired sequence would read <Multi_key> <minus> <a>

Therefore, I decided to replace <macron> with <minus> for all the sequences in the file.

But be careful about editing the file /usr/share/X11/locale/en_US.UTF-8/Compose with sudo!

It is not careful to edit the file /usr/share/X11/locale/en_US.UTF-8/Compose, because it is better to copy it to your home folder, and edit your local version. Copy the file /usr/share/X11/locale/en_US.UTF-8/Compose to .XCompose file in your home folder, by running this command:

```
cp /usr/share/X11/locale/en_US.UTF-8/Compose ~/.XCompose 
```When you have .XCompose in your home folder, the system will use it instead of /usr/share/X11/locale/en_US.UTF-8/Compose

You can edit ~/.XCompose file without sudo privileges or administrative rights. Moreover, if you accidentally mess up the .XCompose file(it may happen), you will still have the original file, /usr/share/X11/locale/en_US.UTF-8/Compose, intact. So you can delete your old ~/.XCompose and start again.

If there are several users on your computer, you should then create ~/.XCompose file for each user individually.

So, the next steps are:
1) To copy the file /usr/share/X11/locale/en_US.UTF-8/Compose into ~/.XCompose
2) To open .XCompose with a text editor and replace all instances of <macron> with <minus> (do it automatically)
3) I recommend putting comments inside the file to make it readable for you later. Comments are preceded with # and a space.
For example:

```
 
# Anatoly replaced all instances of <macron> with <minus>

```The changes will not work until you end your session and log in again, but let us do that later. There is one more thing to do.

The following step will make the system easier to use by adding extra intuitive key combinations that are not present in the original file.

The original file now lets you entrer &#256; by pressing <Compose> <minus> <A> or, alternatively, <Compose> <underscore> <A>.
However, I think it would be better to add some extra combinations: <Compose> <A> <minus> and <Compose> <A> <underscore>. After doing this, you will be able to input &#256; by pressing a hyphen either before, or after pressing A.

So, you add the following lines to ~/.XCompose:

```
<Multi_key> <A> <minus>             : "&#256;"   U0100 # LATIN CAPITAL LETTER A WITH MACRON - added by Anatoly
<Multi_key> <A> <underscore>         : "&#256;"   U0100 # LATIN CAPITAL LETTER A WITH MACRON - added by Anatoly
```Put your name instead of Anatoly.

Below I give some more examples. Those are the characters I use most (Latvian language). You may want to add your own combinations for your own language. Feel free to search inside ~/.XCompose for the letters you need, and think of any sequences you would find easy to use.

&#268;:
    Original combination:
        <Compose> <c> <C>
    My combination:
        <Compose> <C> <C>
Attention! The combination <Compose> <C> <C> will not work because it conflicts with <Compose> <C> <C> <C> <P>
To make it work, disable the latter combination or change it to a different one.

&#274;:
    Original combinations:
        <Compose> <minus> <E>
        <Compose> <underscore> <E>
    My combinations:
        <Compose> <E> <minus>
        <Compose> <E> <underscore>

&#290;
    Original combinations:
        <Compose> <comma> <G>
        <Compose> <cedilla> <G>
    My combination:
        <Compose> <G> <comma>

&#298;:
    Original combinations:
        <Compose> <minus> <I>
        <Compose> <underscore> <I>
    My combinations:
        <Compose> <I> <minus>
        <Compose> <I> <underscore>

&#310;
    Original combinations:
        <Compose> <comma> <K>
        <Compose> <cedilla> <K>
    My combination:
        <Compose> <K> <comma>

&#315;
    Original combinations:
        <Compose> <comma> <L>
        <Compose> <cedilla> <L>
    My combination:
        <Compose> <L> <comma>

&#325;
    Original combinations:
        <Compose> <comma> <N>
        <Compose> <cedilla> <N>
    My combination:
        <Compose> <N> <comma>

Š:
    Original combination:
        <Compose> <c> <S>
    My combination:
        <Compose> <C> <S>

&#362;:
    Original combinations:
        <Compose> <minus> <U>
        <Compose> <underscore> <U>
    My combinations:
        <Compose> <U> <minus>
        <Compose> <U> <underscore>

Ž:
    Original combination:
        <Compose> <c> <Z>
    My combination:
        <Compose> <C> <Z>

&#257;:
    Original combinations:
        <Compose> <minus> <a>
        <Compose> <underscore> <a>
    My combinations:
        <Compose> <a> <minus>
        <Compose> <a> <underscore>

&#269;:
    Original combination:
        <Compose> <c> <c>
    My combination:
        <Compose> <C> <c>

&#275;:
    Original combinations:
        <Compose> <minus> <e>
        <Compose> <underscore> <e>
    My combinations:
        <Compose> <e> <minus>
        <Compose> <e> <underscore>

&#291;
    Original combinations:
        <Compose> <comma> <g>
        <Compose> <cedilla> <g>
    My combination:
        <Compose> <g> <comma>

&#299;:
    Original combinations:
        <Compose> <minus> <i>
        <Compose> <underscore> <i>
    My combinations:
        <Compose> <i> <minus>
        <Compose> <i> <underscore>

&#311;
    Original combinations:
        <Compose> <comma> <k>
        <Compose> <cedilla> <k>
    My combination:
        <Compose> <k> <comma>

&#316;
    Original combinations:
        <Compose> <comma> <l>
        <Compose> <cedilla> <l>
    My combination:
        <Compose> <l> <comma>

&#326;
    Original combinations:
        <Compose> <comma> <n>
        <Compose> <cedilla> <n>
    My combination:
        <Compose> <n> <comma>

š:
    Original combination:
        <Compose> <c> <s>
    My combination:
        <Compose> <C> <s>

&#363;:
    Original combinations:
        <Compose> <minus> <u>
        <Compose> <underscore> <u>
    My combinations:
        <Compose> <u> <minus>
        <Compose> <u> <underscore>

ž:
    Original combination:
        <Compose> <c> <z>
    My combination:
        <Compose> <C> <z>

---

### Post by ellaivarios on 2011-07-27
in a terminal type:

[HTML]xiv[/HTML]then in the little window that will pop up press the key that you are interested in changing.
It will display numbers and info for that key. The number of that key is the keycode map number. For instance my key for the hyphen/minus, underscore key is number 20.

then type:
[HTML]xmodmap -pke | grep 20[/HTML]and don't forget to replace the number twenty above with whatever number corresponds to your key. This will display all the characters associated with this key. The sequence of characters as they appear listed implies their keyboard level for that key. Keyboard levels are:
0.regular (just lowercase characters and numbers)
1.first level (usually pressing Shift to access it, or ShiftLock/CapsLock, for uppercase, etc)
2.second level hidden special characters Accessed with AltGr plus character
3. more hidden special characters. Accessed with AltGr plus Shift plus charcter
4. more hidden special characters. I don't know how to access this level
5. more hidden special characters. I don't know how to access this level

if you install a separate keyboard layout that does not use English, i.e. Greek, then when you switch to this keyboard layout from English (i.e. by pressing CTRL+SHIFT, or whatever you have set it up for), the new keyboard layout will access levels two and three as though they were levels zero and one for it while you type using it, and the original levels zero and one will not be accessible.

so you might get something like this after you type the command I told you above:
[HTML]keycode  21 = equal plus equal dead_macron plus notequal plusminus[/HTML]based on what I told you this means that:

equal is level 0.
plus is level 1.
equal is level 2.
dead_macron is level 3.
plus is level four.
notequal is level 5.
plusminus is level 6.

More clearly:
this means that if you type = and you will get =
then if you press and hold shift and type = you will get +
then if you press and hold the AltGr key and type = and then a vowel, you will get a dead macron, i.e. &#8113;
then if you press and hold the AltGr key+Shift and type = you will get plus
etc.

So, if you switch your keyboard layout from English to something else, it will start with level 2 as though it were its level 0.

Now, if you just want to input macrons over Latin characters, simply use xiv to find out the number of the key you want to change, and then use the following command to make changes to the characters associated with a key and decide which level you want to use for the dead_macron.

NOTE: use "dead_macron" NOT "macron". The second one will just act like a hyphen! It is not a dead key!

The changes are immediate! There is no need to log out.

[HTML]xmodmap -e 'keycode 20 = minus underscore dead_macron underscore emdash'[/HTML]

DON'T FORGET TO CHANGE THE NUMBER 20!!! YOURS WILL MORE THAN LIKELY BE DIFFERENT.

This command above will make a key type a macron when using the AltGr key. If you want to use it with Shift move it one place to the left. If you want it to be a complete dead key, then move it so it is first in the list.

---

