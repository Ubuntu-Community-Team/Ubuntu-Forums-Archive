---
title: "UTF-8 problems from terminal"
date: 2005-05-05
forum: Desktop Environments
---

### Post by kabanta on 2005-05-05
I need to display non-ascii characters in a terminal (at the command line). Even though this (mostly) works at the *application* level on my Hoary install, it does NOT work consistently when viewing files from within a terminal window.

Here is a specific example of the problem. 

- I get an email from someone that contains non-ascii characters (German or Swedish or ...). 

- I can see the non-ascii characters fine within the email application

- Garbage is generated for those characters when I include them in an email reply

- If I view the original email from the command-line, it also displays the non-ascii characters as garbage.

- If I *save* the original email (making *no* changes to it) to a new file and then view it from the prompt, the non-ascii characters display fine.

Obviously, I would prefer not to need to open and re-save every file I get that contains non-ascii characters.

I have:

- run dpkg-reconfigure locales (to include a variety of UTF-8 locales)
- run locale-gen

And, as I say, for the most part, it works. What I am missing?

Any suggestions?

---

### Post by Alexander Kirillov on 2005-05-05
[QUOTE=kabanta]I need to display non-ascii characters in a terminal (at the command line). Even though this (mostly) works at the *application* level on my Hoary install, it does NOT work consistently when viewing files from within a terminal window.

Here is a specific example of the problem. 

- I get an email from someone that contains non-ascii characters (German or Swedish or ...). 

- I can see the non-ascii characters fine within the email application

- Garbage is generated for those characters when I include them in an email reply

- If I view the original email from the command-line, it also displays the non-ascii characters as garbage.

- If I *save* the original email (making *no* changes to it) to a new file and then view it from the prompt, the non-ascii characters display fine.

Obviously, I would prefer not to need to open and re-save every file I get that contains non-ascii characters.

I have:

- run dpkg-reconfigure locales (to include a variety of UTF-8 locales)
- run locale-gen

And, as I say, for the most part, it works. What I am missing?

Any suggestions?[/QUOTE]

How do you "view the original email from the command-line"? Which app do you use? A mail reader such as pine or mutt? Or just plain "mail"? 

Also: can you check which encoding is used in the emails in question? (If you use evolution, go to View-Message Display-Show full headers. There should be a header with encoding information)

My suspicion is that emails you are getting are in latin-1 (aka iso8859-1) encoding. Mail apps such as evolution read the email header, get the encoding, and then  convert the email to UTF8 before displaying or saving to a file. More primitive commands such as "mail" maybe unable to do the conversion. Not sure about Pine and Mutt.

---

### Post by kabanta on 2005-05-05
> How do you "view the original email from the command-line"? In this case, I simply "more" the mail inbox file. (The issue about mail from the command-line has nothing to do with how I *use* email :-) It is just an example of how I *tested* for UTF-8 issues.)

> Which app do you use? A mail reader such as pine or mutt? Or just plain "mail"?  Yes. Means: I've tested with these and others (VM, etc.)

>  Also: can you check which encoding is used in the emails in question? Well, an example email is encoded in UTF-8 -- another using the Swedish ISO localization. 

However, as I mentioned earlier: within the different mail apps, the non-ascii *displays* just fine. It is only an issue a) when including such characters in the reply, and b) from the prompt.  This is why I suspect it has something to do with a setting below the app layer (that the apps are then inheriting).

thanks. k

---

### Post by Alexander Kirillov on 2005-05-05
[QUOTE=kabanta]In this case, I simply "more" the mail inbox file. 
[/QUOTE]
This can be expected to produce garbage if the emails are in  non-urf8 encodings. 

> However, as I mentioned earlier: within the different mail apps, the non-ascii *displays* just fine. It is only an issue a) when including such characters in the reply, and b) from the prompt.  


The problems with replying are indeed puzzling. Does it happen with all email clients? What is your locale?

---

### Post by kabanta on 2005-05-05
> My suspicion is that emails you are getting are in latin-1 (aka iso8859-1) encoding. Actually, with a little more investigation, I think you are correct. The mails that have troubles *are* in iso8859-1. Sorry about that.

Probably I am confused about what I want ...

I have a need to display Swedish and German characters, yet work mostly with English. I assumed that adding UTF-8 localizations for these languages would handle things.

- If I want to reply to emails (or ftp into a server) that is using iso-8859-1 will I be able to see the correct characters if I add that encoding to my locales? (Perhaps even *remove* UTF-8 and use that instead?)

- I have seen reference to LC-* environment variables; my system currently only shows the LANG variable. Is LC necessary? If so, how is it added?

- I do not really understand the interaction between: a) the "desktop language" (that is, the natural language for displaying desktop elements -- set by choosing "language" at login); b) the locale encodinngs set by "dpkg-reconfigure locale"; and c) the LANG variable. (For example, I have done a reconfigure to see if changing the priority of locale encodings made a difference. This had NO effect on the LANG variable.)

Thanks for any suggestions or pointers. k

---

### Post by Alexander Kirillov on 2005-05-05
[QUOTE=kabanta]Actually, with a little more investigation, I think you are correct. The mails that have troubles *are* in iso8859-1. Sorry about that.
[/QUOTE]
If the emails have correct "content encoding" header, then any reasonable mail client should be able to understand them and convert them to otehr encodings  as necessary for display, printing or replying. (Evolution definitely can.) And you can reply to them - your replies are likely to be sent in UTF8 by default, but again, they will have correct headers, so any other conforming mail client shoudl be able to read them. I have done it with emails I received  in iso8859-1, koi8-r, and windows-1251 encodings, all the time using UTF8 myself. 



Trouble is, many emails you may be getting  *do not* have this header (this is violation of standard, but a very common one).
> 
I have a need to display Swedish and German characters, yet work mostly with English. I assumed that adding UTF-8 localizations for these languages would handle things.

- If I want to reply to emails (or ftp into a server) that is using iso-8859-1 will I be able to see the correct characters if I add that encoding to my locales? (Perhaps even *remove* UTF-8 and use that instead?)


As said above, you should be able to read correctly formed emails whether you use iso8859-* or UTF8 encoding yourself. Trouble is with non-conforming emails.  Evolution allows you to manually chose encoding  for each emssage you receive, exactly for such cases. Other clients may behave differently. 

For FTP, I do not know. I try to use only ascii in file names over FTP.
 

> 
- I have seen reference to LC-* environment variables; my system currently only shows the LANG variable. Is LC necessary? If so, how is it added?

- I do not really understand the interaction between: a) the "desktop language" (that is, the natural language for displaying desktop elements -- set by choosing "language" at login); b) the locale encodinngs set by "dpkg-reconfigure locale"; and c) the LANG variable. (For example, I have done a reconfigure to see if changing the priority of locale encodings made a difference. This had NO effect on the LANG variable.)


AFAIK, selecting "desktop language" sets variables LC_* and LANG. 
Normally you should have all of them set; here is output of locale on my system: 
```
kirillov@speonk:~$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

Variable LANG is used as backup: if value of some of LC_* is not set, LANG value is used instead (see, e.g, SuSE docs: [http://www.suse.de/~mfabian/suse-cjk/locales-env-var.html](http://www.suse.de/~mfabian/suse-cjk/locales-env-var.html) for details)

If only LANG is set, something is wrong with your setup...

---

### Post by kabanta on 2005-05-05
> If the emails have correct "content encoding" header, then any reasonable mail client should be able to understand them and convert them to otehr encodings as necessary for display, printing or replying. (Evolution definitely can.)  Sorry I was not so clear earlier. Yes, the emails seem to be well-formed -- and yes, I even setup Evolution to test them and the original mails and replies both display correctly. The issue is that I am not yet willing to switch over to a GUI mail app. :-)

> For FTP, I do not know. I try to use only ascii in file names over FTP. Yes, the file names are not generally a problem. The issue arises if there are "readme" files or the like in non-English languages.

>  AFAIK, selecting "desktop language" sets variables LC_* and LANG. Ah! Your example clarified something. I was using "env" to see the variables; using "locale" shows that I have LC-* variables as well. Thanks.

Well, I'm still not really sure I understand what is going on. For the email: I'm going to dig a bit deeper and see if there is some interaction between the mail client and the MUA. About terminal display, my naive model is that if I set my own system to UTF-8 I should be able to log into a remote system via  terminal, and display text that is encoded in iso-8859-* encoding. If this model is correct, there is something I need to fix in my system. (or perhaps it is a limit of the terminal app itself.)

Again, thanks for all your help. k

---

### Post by Alexander Kirillov on 2005-05-05
[QUOTE=kabanta]About terminal display, my naive model is that if I set my own system to UTF-8 I should be able to log into a remote system via  terminal, and display text that is encoded in iso-8859-* encoding.[/QUOTE]

I am afraid not. If you login (say, via ssh) to a system that itself uses iso8859-* encoding, and try, say, "man" command, I'd expect it will produce output in iso8859-*, which will be sent "as is" -- no conversion - to your terminal and thus, non-ascii symbols will look like garbage.

---

### Post by kabanta on 2005-05-06
Ah, of course!  I've now spent some time looking for terminal emulators that are a bit smarter about converting what they get. The aterm emulator seems to do a reasonable job. Now, to solve my email problems ....

Thanks again for all the help. k

---

