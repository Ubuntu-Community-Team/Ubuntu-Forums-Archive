---
title: "auto firefox full screen and lock at startup"
date: 2010-01-02
forum: Desktop Environments
---

### Post by mepatuhoo on 2010-01-02
i am working on a project where we will be setting up a system, where i want it to run ubuntu and at start up auto start firefox in full screen mode with nothing showing that its in firefox and lock it so the user can not get out of full screen mode from the F11 key. This system will be only used for this one program that i am building it would be nice to have a way to get out of full screen with a password for repair if needed but prevent the user from being able to access anything outside of the application. this is going to be a web application as you could guess by using firefox but there is nothing on the web showing how to set up a system where i can lock the system into a firefox full screen mode with a pre-set web URL pointing to the application that i am building. can some one direct me to some handy configuration instructions for making a secure set-up like this for the system. the system will be a cheap small pc that will only be running the one firefox web application we have been looking into using a touch screen so that the user will not need a mouse and keyboard, i have not used a touch screen before and also wanted to know if a touch screen can easily work with firefox. thank you for your help.

---

### Post by PhrankDaChickenGeek on 2010-01-02
I use the R-Koisk extension for Firefox for my full-screen webapps: [https://addons.mozilla.org/en-US/firefox/addon/1659](https://addons.mozilla.org/en-US/firefox/addon/1659)

You can add "firefox URL" to "Startup Applications" (Sys -> Prefs) , and set the user to automatically log in in "Login Screen" (Sys -> Admin) to make it auto start

You might also want to lock down some GNOME settings - [http://library.gnome.org/admin/deployment-guide/](http://library.gnome.org/admin/deployment-guide/)

I haven't used touchscreens in Ubuntu, so I wouldn't know about that

---

### Post by mepatuhoo on 2010-02-22
it looks like prism may be the solution to this. it gets the extra stuff out of the way and i was able to switch the json data to make the screen go into full screen mode. so if anyone else is looking for something like this look at prism, it runs on the same rendering engine as firefox.

---

### Post by mepatuhoo on 2010-02-22
[http://prism.mozilla.com/](http://prism.mozilla.com/)

---

