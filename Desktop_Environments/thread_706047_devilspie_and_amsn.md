---
title: "devilspie and amsn"
date: 2008-02-24
forum: Desktop Environments
---

### Post by notepad on 2008-02-24
amsn always opens its main window in the top left of my screen when i want it in the top right.
it also opens chat windows in the top left when id prefer them to be more central.

ive made two *.ds files contained in ~/.devilspie/  as listed below;

amsn.ds

(if
	(and
		(is (application_name) "amsn")
		(contains (window_name) "aMSN")

		 (geometry "x264x432+1144+46")
	)
)





amsn.chat.ds

(if
	(and
		(is (application_name) "Amsn")
		(contains (window_name) "Chat")
	)
	(geometry "+140+140")
)




neither of these files have any effect on amsn. note that i have made a ds file for virtualbox which works perfectly.

i have used xwininfo and xprop to find properties of amsn windows and ive tried all kinds of things. i did manage to get chat windows to open where i want by using 

(is (window_role) "msg_0")

the only trouble with that was, it took my taskbar to that location as well. i figured i would have to use an AND operator to check 2 conditions before it matched the window to prevent the taskbar from being relocated.

i will keep playing with this to see if i can get it right. if i do i will post the contents of the ds files here.

in the meantime i will be happy to hear from anybody who has any ideas.

---

### Post by notepad on 2008-02-24
ive made the ds files simpler and got some working results;

amsn.ds

(if
		(contains (window_name) "aMSN")
		(geometry "264x432+1144+46")
)




amsn.chat.ds

(if
	(contains (window_name) "Chat")
	(geometry "490x400+180+140")
)


the only problem i can see with these is that if another window should ever open with
a string matching those listed above in the window title, the window will be matched
and its geometry adjusted accordingly. i had wanted to do something more specific with
these files to eliminate that possibility.

im noticing some syntax errors in my original amsn.ds file which would no doubt have stopped it from working. when i get some spare time i will play with the boolean AND operator again to see if i can create a more specific set of conditions before matching a window.

my next plan for devilspie is to get it to send virtualbox to say desktop 3 in fullscreen mode(or something that looks like it) and workout how to change desktops while the mouse and the keyboard are being captured by the guest OS.

---

