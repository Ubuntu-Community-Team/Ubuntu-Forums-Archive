---
title: "Accidently deleted Desktop Pager"
date: 2011-07-10
forum: Desktop Environments
---

### Post by held7over on 2011-07-10
Lubuntu 10.10  I was trying to increase the number of workspaces from 2 to 4 and not having any luck, when I accidentally deleted desktop pager on my task bar. (I am assuming that is the name of the visible workspace switcher on the task bar where at a glance you can see you have other things on other desktops.)

I brought up Add/Remove Panel Items, but Desktop Pager was no longer listed! 

How do I get the workspaces switcher back on the task bar? And how can I increase the number of workspaces it is showing?

Thanks!  :)

---

### Post by SteveDee on 2011-07-11
> **held7over said:**
> ...How do I get the workspaces switcher back on the task bar? And how can I increase the number of workspaces it is showing?

 - Right click on a blank area of the panel.
 - Select Add/Remove panel items.
 - In Panel Preferences click the "Add" button.
 - Select Desktop Pager from the list and click "Add"
 - With Desktop Pager highlighted in Panel Preferences, use the "up" and "down" buttons to move to required position.
 - With Desktop Pager highlighted click on the "Edit" button.
 - Select the number of desktops you require.

---

### Post by held7over on 2011-07-11
Thanks SteveDee!

It worked! I have the pager back and in it's correct position. 

--Except when it came time to edit the highlighted Desktop Pager to increase the number of workspaces......the "edit" button is greyed disallowing me to perform the edit.

Any ideas on how to convince it otherwise?

Thanks!

---

### Post by held7over on 2011-07-11
For anyone following this thread, I found the final solution to my edit problem in increasing the number of workspaces.

First, RIGHT click the desktop and drop down the menu and LEFT click "Desktop Preferences". Then SELECT the "Advanced" tab. Then ENABLE show menus.

Second, RIGHT click the desktop and drop down the menu and LEFT click "Desktops". Then slide over and down to LEFT click "Add new desktop". Click "Add new desktop" for as many new workspaces as you require.

---

### Post by SteveDee on 2011-07-11
> **held7over said:**
> ...Any ideas on how to convince it otherwise?

I don't know why that should be.

You can also try menu "Preferences" > "Openbox Configuration Manager" > "Desktops"

If that doesn't work, but you're still very keen to change the number of desktops, you could try opening /home/{user name}/.config/openbox/lubuntu-rc.xml and editing desktops directly. The bit of the file you are looking for looks like this:-
```

  <desktops>
    <!-- this stuff is only used at startup, pagers allow you to change them
       during a session

       these are default values to use when other ones are not already set
       by other applications, or saved in your session

       use obconf if you want to change these without having to log out
       and back in -->
    <number>2</number>
    <firstdesk>1</firstdesk>
    <names>
      <!-- set names up here if you want to, like this:
    <name>desktop 1</name>
    <name>desktop 2</name>
    -->
    </names>
    <popupTime>875</popupTime>
    <!-- The number of milliseconds to show the popup for when switching
       desktops.  Set this to 0 to disable the popup. -->
  </desktops>

```
After changing the number, add or remove <name>desktop lines to match. Then log out/in and see what happens. This probably wont work, but if you are confident with this kind of edit, its worth a try.

Edit:-
> 
For anyone following this thread...

...sorry! our posts crossed...

---

### Post by held7over on 2011-07-11
Actually, SteveDee I wrote my SOLVED too soon. My fix on the number of desktops disappears upon shutdown. When I boot back up, there are just 2 desktops again.

I am going to try your two solutions. I will make another entry and tell you what happened. But it will be a few hours before I can try it.

Thanks for your efforts. They look like good things to try!

---

