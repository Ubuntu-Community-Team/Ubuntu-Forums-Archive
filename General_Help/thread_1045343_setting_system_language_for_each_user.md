---
title: "setting system language for each user"
date: 2009-01-20
forum: General Help
---

### Post by El-ahrairah on 2009-01-20
as the topic title says, is it possible to set the system language to be used for each single user?

I have a laptop with ubuntu 8.04.1 on it, and there are two users on it: my dad and me. My dad prefers to have it in italian, while I prefer to have it in english. would it be possible to configure it so that when I log in, it sets the language to English, and when my dad does, it is set to italian?

thanks

---

### Post by schilcha on 2009-01-20
This worked for me:
o) at the login screen, enter your username (and press enter)
o) go to one of the settings-menu and look for the option to change the language (the position of this menu might vary from one gdm-theme to another)
o) select the language of your choice
o) answer the question (cannot recall the text right now) asking whether you want this as default login-screen-language (I think;)
o) enter your password and enjoy the system in your preferred tounge.

btw: you might need to install additional language packages. I did this via System -> Settings -> Language Support

Good Luck,
   schilcha

---

### Post by El-ahrairah on 2009-01-21
so in this way EACH user can have its preferred language? I'll try it ASAP, thanks!

---

### Post by El-ahrairah on 2009-01-22
I tried your solution, but it seems to not be working... if, for example, user2 logged in using Italian language, the next time I log in with user1 in English I get a prompt to set italian as default language, and I can only choose "for this session only" or "make default"

---

### Post by schilcha on 2009-01-22
Hm, I just tried the whole process again and have to admit that my previous posting was a little inaccurate -- sorry for that.

Upon selecting a new language (after having entered the username, so gdm knows for which user to set the language), TWO questions were asked:
1) Do I want to restart gdm to have the login screen in the new language as well. I declined.
2) Do I want to use this new language *my* new default language or only for this session. I chose "make default". 

> **El-ahrairah said:**
> [...] user2 logged in using Italian language, the next time I log in with user1 in English I get a prompt to set italian as default language, and I can only choose "for this session only" or "make default"

If you choose "make default" for the second question, the login screen will remain Italian, but your session will be in English (I hope).

---

### Post by El-ahrairah on 2009-01-23
> **schilcha said:**
> Upon selecting a new language (after having entered the username, so gdm knows for which user to set the language), TWO questions were asked:
1) Do I want to restart gdm to have the login screen in the new language as well. I declined.
2) Do I want to use this new language *my* new default language or only for this session. I chose "make default". 

I did exactly the same thing, trying to set Italian for user2.

But then, when I try to log in with User1, I get a window saying that the last language used for last login was English, and now default language is italian, and it asks me if I want to make English my default language.
If I select "make default", then I'll get a similar prompt for user2... So I guess I'll just keep using "for this session only"

---

