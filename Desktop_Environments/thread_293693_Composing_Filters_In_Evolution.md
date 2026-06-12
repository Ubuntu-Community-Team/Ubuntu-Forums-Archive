---
title: "Composing Filters In Evolution"
date: 2006-11-05
forum: Desktop Environments
---

### Post by alec on 2006-11-05
Hi 

I am a new user of Unbuntu Edgy with Evolution 2.8.1 and new to Gnome 

I am following a how to which should enable me to use bogofilter with evolution. 

To do this I have to add two filters which use 'pipe to program'. The problem is that the add filter menu will only allow me to give the path to bogofilter, it will no allow me to give a -s or -u extensions to the command.

I can get "pipe to program /usr/bin/bogofilter" but cannot write the command "pipe to program /usr/bin/ bogofilter -s" or -u

All of the how to's in this area, that I have found searching the forum. Show what I take to be an older version of Evolutions dialogue box for writing filters, and I cannot work out how to write the proper commands in the version I have 2.8.1.

Any help in this matter would be greatly appreciated,

Alec

---

### Post by Mau on 2006-11-05
I too am interested in this.

---

### Post by JamesWP on 2006-11-06
Hmm, been searching around for this aswell, only thing i've came close to is this from a [bug report]("http://bugzilla.gnome.org/show_bug.cgi?id=354797#c5").

> Since your parameters are all constant, Write a simple script that will get
some arguments and call the individual bogofilter and spamassasin scripts with
required arguments. And set this script to be executed in the filter. This
should solve your problem. 

Bit of a Linux newbie so I'm not sure how to go about creating a script to do such, any ideas? :)

---

### Post by Spin Doctor on 2006-11-20
[FONT=Verdana]Good news guys, I have found the solution to this problem.

The problem is the following: **Spamfiltering will not work out-of-the-box  in Evolution 2.8.1**, which is installed with Edgy. Most how-to on the web explains the "pipe to command" solution to solve this. However on Evolution 2.8.1, this option does not exist. 

I am running the swedish locale, so I have tried to translate the selections as close as possible so will find the relevant selection on your system.
[/FONT][LIST=1]
[*][FONT=Verdana]First make sure you have bogofilter and spamassain installed on your system. You can make a quick search on Synaptic to make sure.[/FONT]
[*][FONT=Verdana]Make sure you have checked both bogofilter and spamassasin plugin modules in evolution.[/FONT]
[*][FONT=Verdana]In your settings on evolution>>emailsettings>>spam tab: Make sure both options are checked.
[/FONT]
[*][FONT=Verdana]Create a filter, which you place before any other filters. Make sure it is on incomming mail.[/FONT][LIST]
[*][FONT=Verdana]Make sure, all conditions apply is selected[/FONT]
[*][FONT=Verdana]Add condition, "junkmailtest"[/FONT]
[*][FONT=Verdana]Select, "if mail is junk"[/FONT]
[*][FONT=Verdana]Continue to next  box, which is "then"[/FONT]
[*][FONT=Verdana]Add set status = read[/FONT]
[*][FONT=Verdana]Add set status = is junk[/FONT]
[*][FONT=Verdana]Set color = red (to easily see which has been determined)[/FONT]
[*][FONT=Verdana]Save filter[/FONT][/LIST] 
[*][FONT=Verdana]Now you need to train the filters properly. The key is to be able to let the filters know some emails which are not spam. What you need to do is to mark maybe 30 or so legite emails you have in your inbox as spam. (ctrl+j) These emails will then end up in your spam folder.[/FONT]
[*][FONT=Verdana]The key now is to go to the spamfolder, and mark all these emails as "not junk" (shift+ctr+j).[/FONT]
[*][FONT=Verdana]Now your spamfilter is activated, but it needs to continue its training. As you go on, keep an eye on your spamfolder to recognize and "sort back" non-junkmail which might been caught there and continue to keep on marking mail that is spam in your inbox which the filters did not catch.[/FONT]
[*][FONT=Verdana]As I feel it, you will always have to continue to train your filters since spammers are always coming up with new tricks, but for me I am glad to see the junkmail is catching allready 95 % after a couple days of training.
[/FONT][/LIST][FONT=Verdana]Hope this helps! Greetings from Sweden![/FONT]

---

### Post by dpm on 2006-11-20
> **Spin Doctor said:**
> [FONT=Verdana] "pipe to command" solution to solve this. However on Evolution 2.8.1, this option does not exist. [/FONT]

That's not correct. The "Pipe To Program" is still where it always has been, see the screenshot.

You are right in saying that Evolution is not installed with spam filtering per default, but AFAIK all you have to do in order to activate spam filtering is 1) to install either _spamassassin_ or _bogofilter_ (or both if you like belt-and-braces solutions), 2) go to **Edit>Plugins** and activate the antispam plugins you like (i.e. either _spamassassin_, _bogofilter_, or both, depending on your choice) and,

3) After that, spam filtering will not still work straight away. You'll have to train the filtering program so it can learn to distinguish spam from ham (i.e. legitimate e-mail). IIRC, the filter won't have learnt properly until it has filtered about 100 spam messages and 100 ham messages (note: search the evolution mailing list for more accurate information, it is always a good source). 

The way you train the spam filter is to manually mark the messages you want as spam with the **"Junk" button** (or its equivalent key shortcut) on the Evolution's toolbar. If you or the filter marked some legitimate messages as spam, you simply go to the **"Junk" folder** and press the **"This is not junk" button** (or its equivalent key shortcut) having selected the message.

---

### Post by Spin Doctor on 2006-11-21
Well, you are right about "pipe to command" option still being there. Thanks for pointing this out. What I meant to say is that you cant send any commandline parameters with the "pipe to command" option, which u could do in earlier versions of Evolution. The only thing you can do is to click the "browse" button,select a program, and then select if return 1 do this etc.

---

