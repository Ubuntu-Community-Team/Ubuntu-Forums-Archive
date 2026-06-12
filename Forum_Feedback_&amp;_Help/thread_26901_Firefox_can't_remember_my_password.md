---
title: "Firefox can't remember my password"
date: 2005-04-14
forum: Forum Feedback &amp; Help
---

### Post by JuanC on 2005-04-14
Hi to all ,

I use Firefox and I love one functionality that Firefox remembers all login and passwords that i use for my websites.

But in this forums , **Firefox didn't remember my password** only remember my login.

I see that when i type my password and click into login , the password is cleaned and i think this is why firefox can't store it.

When this bug in the forums would be fixed ?

---

### Post by kassetra on 2005-04-14
[QUOTE=JuanC]
I see that when i type my password and click into login , the password is cleaned and i think this is why firefox can't store it.

When this bug in the forums would be fixed ?[/QUOTE]

Ok, first of all, it's not a bug in the Forums.  

It's possibly a bug in the way you told firefox to remember your information.  If you told firefox to never remember the password for this site, but yet accepted the cookie from the site, and told the site to remember you - 

You would have a login screen with your name and no password each time.  

To fix the problem, you'd need to remove the forum site from your list of sites in firefox and then come to the forums again, and tell firefox to remember your password.

---

### Post by JuanC on 2005-04-14
[QUOTE=kassetra]Ok, first of all, it's not a bug in the Forums.  

It's possibly a bug in the way you told firefox to remember your information.  If you told firefox to never remember the password for this site, but yet accepted the cookie from the site, and told the site to remember you - [/QUOTE]

This doesn't the problem , I delete the site from the list and i went to the site i type the same and FireFox only remenber login i try it several times.Always said yes to FireFox store it.

Because of this , i saw that when you type the password and click into login , the password is cleaned and i think save into other variable and send to the server.

I think this is a bug , because , if the forum cleaned the password , FireFox wouldn't remember it.

When this bug in the forums would be fixed ?

---

### Post by kassetra on 2005-04-14
[QUOTE=JuanC]
Because of this , i saw that when you type the password and click into login , the password is cleaned and i think save into other variable and send to the server.

I think this is a bug , because , if the forum cleaned the password , FireFox wouldn't remember it.

When this bug in the forums would be fixed ?[/QUOTE]

No, it is not a bug in the forums, firefox cleans out a password if you told it to NOT remember the password.

You have to remove the site from the list of sites you've told firefox to remember passwords for, dump your cache, and then shutdown and restart firefox.

If this were a bug in the forums, none of us would be able to keep signed on.

---

### Post by JuanC on 2005-04-15
[QUOTE=kassetra]No, it is not a bug in the forums, firefox cleans out a password if you told it to NOT remember the password.

You have to remove the site from the list of sites you've told firefox to remember passwords for, dump your cache, and then shutdown and restart firefox.

If this were a bug in the forums, none of us would be able to keep signed on.[/QUOTE]

But i tell to FireFox to remember it.

Have you got FireFox ?

My FireFox version is 1.0.2 and the password manager only don't remenber password in this site.

When in the preferences tab in privacy i select to show all logins and passwords , only in this site the password field is null and the login is store correctly.

I try that you say a lot of times and the password manager don't store it , i shutdown and restart firefox also.

I don't say that anybody can sign-on , i only say that you **have to** type it manually because the password manager don't remenber the password.

---

### Post by jensyt on 2005-04-15
It happens because vBulletin uses Javascript to clear the password field right after you press either enter or "Login" (or whatever the button is).

Firefox only saves it **after** the input is cleared, and thus you have a problem.

---

### Post by lao_V on 2005-04-15
I have no problem on saving my password for this forum in firefox/konqueror on my pc at work and home!!!

---

### Post by JuanC on 2005-04-15
[QUOTE=jensyt]It happens because vBulletin uses Javascript to clear the password field right after you press either enter or "Login" (or whatever the button is).

Firefox only saves it **after** the input is cleared, and thus you have a problem.[/QUOTE]

Thanks jensyt , I think this is the bug.

---

### Post by jensyt on 2005-04-15
[QUOTE=lao_V]I have no problem on saving my password for this forum in firefox/konqueror on my pc at work and home!!![/QUOTE]
Do you have Javascript enabled? And just to clarify, he's trying to use Firefox's password-saving features, not vBulletin's use of cookies to remember your login.

[QUOTE=JuanC]Thanks jensyt , I think this is the bug.[/QUOTE]
I wouldn't call this a bug; I'm fairly certain it's meant to be a security feature. Disable Javascript for that one time you want to login and have it remember, and it **may** work. I can't make promises, though, since I'm not too well-versed in vBulletin's inner workings.

---

### Post by JuanC on 2005-04-15
> Disable Javascript for that one time you want to login and have it remember, and it may work

Thanks jensyt

It works the fist time i do , if the second time you have enable javascript , the password were stored as null ...

I am becoming crazy  ](*,) 

It so a mess that to enter to this forum , i have to disable javascript , it's more easy that the forum disable the option to clean the pass.

---

### Post by kassetra on 2005-04-15
I'm using Firefox with Javascript, and I have none of those problems.  It never fails to remember my password, and I never have to type either my username nor my password in.

The only time I've ever experienced this kind of issue is when the password manager list was upgraded from one version to the next.  I had to manually go in and clear out all of the sites where this happened and then visit those sites again with my upgraded Firefox and tell it to remember them.

---

### Post by JuanC on 2005-04-20
I saw that is not only my problem  :

[https://bugzilla.mozilla.org/show_bug.cgi?id=257781](https://bugzilla.mozilla.org/show_bug.cgi?id=257781)

---

### Post by Adler on 2006-09-02
Hi All,

I'm trying make sure that I can back-up my Bookmarks (which I can), **and** all my Web Site login / passwords that would also include cookies.

I'm sure that IE @ one point gave me this function, but I never seem to be able to do it w/ FF.

Backing up /Home is easy -- any ideas?

Adler

---

### Post by omns on 2006-09-02
.

---

### Post by stevieb on 2006-09-02
> 
To fix the problem, you'd need to remove the forum site from your list of sites in firefox and then come to the forums again, and tell firefox to remember your password.

I have the same problem, and the above solution doesn't work- these forums are not listed in either Passwork Manager window.

Any way to add them in?  There doesn't seem to be an 'add' function anywhere.
-steve

---

### Post by Adler on 2006-09-03
> Backing up the your ~/.mozilla folder should do what you need. To restore just copy this folder into your new home directory.


manicka,

Thanks for that, and thanks for the Welcome. I love thos guys over in SuSELand. But, it was time to move on...

Adler

---

### Post by slimdog360 on 2006-09-04
it works for me in all firefox's but in the new firefox2 beta2 it stores al those passwords which couldnt be stored before.

---

### Post by wlad0 on 2009-09-07
Check your exceptions for Remember passwords for sites. If is page in list, remove it. Edit -> Preferences -> Security

---

### Post by Adler on 2009-09-07
Hi All,

I was using something a FF extension called "Foxmarks", the name has been changed to "Xmarks". 

It saves all my bookmarks, toolbar, and passwords.

You can get it [here]("http://www.foxmarks.com/").

Best Regards,

JJMacey
Phoenix, Arizona

---

### Post by -grubby on 2009-09-07
> **wlad0 said:**
> Check your exceptions for Remember passwords for sites. If is page in list, remove it. Edit -> Preferences -> Security

I think at this point he's already solved it.

---

### Post by Perfect Storm on 2009-09-07
...and with that the thread will be closed due to necromancing (2005).

[img]http://www.imageviper.com/displayimage/142275/0/necromancer.png[/img]

R.I.P.

---

