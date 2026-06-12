---
title: "Log active windows"
date: 2011-04-08
forum: Desktop Environments
---

### Post by JHorrocks on 2011-04-08
I am running ubuntu desktop 10.10 and would like to know where do I start in creating an app or script that can log my active windows.

What I mean by that is if I open firefox, I want it to write to a txt file the application name "firefox" and the datetime the window was active/set focus on.

If I minimize/close/unfocus firefox, it then writes to the txt file the datetime the window was minimize/closed/unfocused etc...

Why do I need this?

When I am doing a project for a company (I am a web developer) it is good to know how much time I spent on project planner/monodevelop/mysql/photoshop etc...

I have an existing app that I have used for years but i built in for windows, but now I have shifted over to Ubuntu (best thing I ever did!).

My existing app just appends to a daily txt file:
1 - the active window application name (ie.. MonoDevelop)
2 - the window application title (ie. MonoDevelop - Test Project 1)
3 - datetime the window was active
4 - datetime the window was set minimize/closed/unfocused/inactive

From there I can then generate a weekly report grouping by application, application title and how much time was spent on the active window.

PLEASE NOTE:
I am not interested in keyloggers, screenshot spy stuff, this is to only help me bill out my time (although its not 100% accurate, ie... if I go to the toilet and leave the active window open, i charge my client 5 mins more than I should etc...) it is only a rough (and I mean very rough) guideline for me.

Where do I start? 

I will be using Mysql to import the txt files to group the apps, report etc... I dont need advice on that, just the "HOW TO" record active windows to txt files.

Any pointers in the right direction would be greatly appreciated.... :)

---

### Post by JHorrocks on 2011-04-12
Anyone with any pointers in the right direction, or have I posted in the wrong forum?

---

### Post by DoomChisel on 2011-10-11
Yes, today on my Windows 7 i've got TimeTracker <[http://sourceforge.net/projects/ttracker/]("http://sourceforge.net/projects/ttracker/")>, it does the thing you've described...

And now think that such functionality is really cool and underestimated today.
Have you any success with search for such tool under GNU/Linux?

---

### Post by JHorrocks on 2011-11-08
hmm, but the problem is I am on ubuntu 11.10 not windows 7. My code already works on windows 7.

I have decided to use monodevelop and install mono so that I can create a gtk app, I just need to find out how to detect the current active window using monodevelop lib's

Basically I am trying to find the equivalent to:

[DllImport("user32.dll")]
static extern IntPtr GetForegroundWindow();
	
[DllImport("user32.dll")]
static extern int GetWindowText(IntPtr hWnd, StringBuilder text, int count);

Any help would be greatly appreciated (I am using Unity 11.10 desktop)

---

### Post by DoomChisel on 2011-11-10
I have no experience in programming GTK or X Server, but, maybe, these can help:
[list]
[*] [http://www.xfree86.org/4.0/XGetInputFocus.3.html](http://www.xfree86.org/4.0/XGetInputFocus.3.html)
[*] &#10216;...&#10217;
[*] [http://stackoverflow.com/questions/2041532/getting-pid-and-details-for-topmost-window](http://stackoverflow.com/questions/2041532/getting-pid-and-details-for-topmost-window)
[*] [http://stackoverflow.com/questions/1201179/how-to-identify-top-level-x11-windows-using-xlib](http://stackoverflow.com/questions/1201179/how-to-identify-top-level-x11-windows-using-xlib)
[/list]

BTW, can you release your Windows application (this would be better with source code)? TimeTracker seems to need some changes to fit my needs, but i don't want to get deep into code.

---

