---
title: "HELP: Panel media control buttons?"
date: 2007-08-10
forum: Desktop Effects &amp; Customization
---

### Post by thebigham on 2007-08-10
How can i get media buttons like that on the panel that can control Amarok? 

[IMG]http://img523.imageshack.us/img523/4500/innocentstuffbyneedcof2bf3.jpg[/IMG]

I found that at [http://www.deviantart.com/deviation/44317193/?offset=25](http://www.deviantart.com/deviation/44317193/?offset=25)

It has a readme file in there, but it doesnt work with Ubuntu. :(

> 
sure, it is very easy.

1st. copy or move these folder (Mediabuttons) to a directory of your choice
2nd. create a new launcher at your panel like so:
	- right-click on any vacant space on the panel
	- choose "Add to Panel"
	- select "Custom Application Launcher" from the list
	- fill in the fields like this (for the play-button)
		Name:		name for the launcher eg. play
		Comment:	here you can add a comment that will displayed in a tooltip
		Command:	listen --play-pause (this is the command that will execute,
				"Listen" and will play / pause in this example)
		Icon:		this is the place where you select to the play-button by
				browsing to the Mediabuttons directory or simply drag & drop it

just do these steps for the other buttons with the associated commands and mediabuttons (listen --next, listen --previous for "Listen")

for other programs please take a look at its man-page

hope that helps :)


---

### Post by thebigham on 2007-08-11
Can anyone please help me with this? Am i not explaining it right? I have been using something called [True Launch Bar]("http://www.truelaunchbar.com/plugins/winamp.html") in Windows XP for a long time, and it was very useful to me.  Is there anything similar in Ubuntu?

---

### Post by thatonefatguy on 2007-12-20
idk if your still trying this but i figured it out.
I was searching for something like this for awhile now.
I was trying to do it for Banshee but i had no luck with that.
Anyway the whole thing with this is you have to be using the Listen music player.
Just install that and then follow the directions for the read me and it should work fine.
Mine seems to have a small delay but nothing major.

---

