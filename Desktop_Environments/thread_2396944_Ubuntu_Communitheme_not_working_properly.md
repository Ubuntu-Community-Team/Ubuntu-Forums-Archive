---
title: "Ubuntu Communitheme not working properly"
date: 2018-07-23
forum: Desktop Environments
---

### Post by new+gen on 2018-07-23
I installed **communitheme** using snap.
This how it supposed to look : [https://imgur.com/a/IOiZM2y](https://imgur.com/a/IOiZM2y)
As you can see Ubuntu logo must be in Bottom Left Corner. It is used as app drawer icon

But this is how Communitheme looks in my computer : [https://imgur.com/a/3zA3AYt](https://imgur.com/a/3zA3AYt)

The ubuntu logo is placed at Top Left Corner and it is near Activities tab. The logo is small and there are no functionalities for it .
How can  I fix this??

Just in case you wonder , in login screen I only have two Desktop environment options : "Ubuntu" and "Ubuntu  Communitheme-snap"
Please help me fix this .

---

### Post by PaulW2U on 2018-07-23
Hi new-gen, the Communitheme is still a "work in progress". It's still being developed, bugs are being fixed and design changes are being finalised. Communitheme won't even be the name that it is known by when it is released. I understand that it will be the default theme for Ubuntu 18.10.

You can find more information on the [Community Hub]("https://discourse.ubuntu.com/c/desktop") where you'll also find links to where you can report any bugs that you find.

Better links:
[Call for participation: an ubuntu default theme lead by the community?]("https://discourse.ubuntu.com/t/call-for-participation-an-ubuntu-default-theme-lead-by-the-community/1545")
[CommuniTheme Progress]("https://discourse.ubuntu.com/t/communitheme-progress/5924")

---

### Post by #&amp;thj^% on 2018-07-23
Please be aware that you may encounter numerous issues when using Ubuntu communitheme as this is also a reason why Communitheme was not selected as a default theme for Ubuntu 18.04 LTS release. 
the theme is already available to install and try out — just keep in mind that there will be bugs, rough edges, inconsistencies, unstyled elements, and so on.
Also Read:[https://github.com/Ubuntu/gnome-shell-communitheme](https://github.com/Ubuntu/gnome-shell-communitheme)
> This is a very early pre-release version of the theme. This package is intended for the Communitheme designers to get a sense of what actually works in Ubuntu. Many icons are missing, some stuff is just a white squircle. You will find issues and stuff will break. We'll make a public statement when this theme is ready for a wider audience.
Also if you want to participate see this: [https://community.ubuntu.com/t/call-for-participation-an-ubuntu-default-theme-lead-by-the-community/1545/1584](https://community.ubuntu.com/t/call-for-participation-an-ubuntu-default-theme-lead-by-the-community/1545/1584)
Ninja'd by PaulW2U :)

---

### Post by new+gen on 2018-07-23
is it that unstable ? 
Do I need to switch to default Desktop Environment ????
I use my computer for learning programming and Android Development.

---

### Post by PaulW2U on 2018-07-23
> **new+gen said:**
> is it that unstable ? 
Do I need to switch to default Desktop Environment ????
I use my computer for learning programming and Android Development.
Personally I found it very usable but it is known to be buggy and design decisions change on a weekly basis. An [updated snap]("https://discourse.ubuntu.com/t/call-for-participation-an-ubuntu-default-theme-lead-by-the-community/1545/1594") of the theme was released just this afternoon. In fact there's a new release every Monday afternoon. Just don't expect the theme to work perfectly with every application just yet. They're still working on the position of the Ubuntu logo and I'm not sure if it will have any functionality other than to identify the desktop as being Ubuntu. That may change of course.

By all means continue to use the theme. 1fallen and I just wanted to point out that it's unfinished and your questions may be better answered by reading the respective threads that we linked to earlier.

If you haven't already been automatically updated to version 0.1 (644) of the theme then
```
sudo snap refresh communitheme
```
will update you to today's release.

---

### Post by Frogs Hair on 2018-07-23
The latest cosmetic changes caused me to stop using communitheme though it has been stable. I'll login again next week to see the latest changes ;). As written it's a work in progress though the logo and activities button having the same function didn't make sense to me.

---

### Post by PaulW2U on 2018-07-24
Latest update - [Open The Cosmic Gate: A beautiful theme gets a beautiful name ]("https://didrocks.fr/2018/07/24/open-the-cosmic-gate-a-beautiful-theme-gets-a-beautiful-name/") confirming:

[LIST]
[*]A new name for the theme - **Yaru**
[*]Ubuntu 18.04 users need to continue uisng the snap
[*]The theme will be available in the repositories from 18.10 onwards
[*]Updates will continue on a weekly basis
[*]Keeping the Ubuntu logo on the launcher is something that is still to be decided
[/LIST]

---

