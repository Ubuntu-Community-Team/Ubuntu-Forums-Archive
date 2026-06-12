---
title: "Terminal problems &lt;newbie&gt;"
date: 2006-02-03
forum: Desktop Environments
---

### Post by riwa on 2006-02-03
I've got some problems with my terminal. The following are the vital ones.

Downloading thru terminal. For some unknown reason by downloading rate is way better when using the Terminal than the GUI. Noticed when using SPM vs Terminal.
So... How do I use the terminal to download? Tried some things like: 
apt-get install *address* 
but I just get an errormessage. What's the correct syntax?

Also:
after setting TERM=gnome-terminal:
I can't use clear. 'gnome-terminal' is not recognised. 
I can't use info *command*. 'gnome-terminal' or 'dumb' is not smart enough to use info.
I need to restart the terminal and reset TERM to NULL to get it to work again. 

I simply set it by TERM='gnome-terminal' ; export TERM.

Finally:
I've set an: 
*alias ls='echo ; ls ; echo*
in my .bashrc script which works fine unless I try to invoke it with options. Any suggestions here?

By the way which is the file where i set my login stuff etc. Tried create a .login but didn't work (unless i did it wrong)..

Regards
Richard

---

### Post by joft on 2006-02-07
> **riwa]Downloading thru terminal. For some unknown reason by downloading rate is way better when using the Terminal than the GUI. Noticed when using SPM vs Terminal.
So... How do I use the terminal to download? Tried some things like: 
apt-get install *address* 
but I just get an errormessage. What's the correct syntax?[/QUOTE]

I'd suggest

```
wget <URL>
```

for this. Or what do you mean? apt-get is for package management only.

[QUOTE=riwa]Also:
after setting TERM=gnome-terminal:
I can't use clear. 'gnome-terminal' is not recognised. 
I can't use info *command*. 'gnome-terminal' or 'dumb' is not smart enough to use info.
I need to restart the terminal and reset TERM to NULL to get it to work again. 

I simply set it by TERM='gnome-terminal'  said:**
> 

AFAIK gnome-terminal uses "xterm" for the TERM env variable. Why do you want to change this? Isn't it set?

[QUOTE=riwa]By the way which is the file where i set my login stuff etc. Tried create a .login but didn't work (unless i did it wrong)..

Do you mean one of the files ".bashrc" or ".bash_profile" or ".bash_login" ? I assume you have got installed bash ...

---

### Post by caven80 on 2006-02-07
hello experts

Im sorry..this is no a reply to this post..i'm a newbie myself..can some please tell me where can i submit a NEW POST..

sorry for being this naive..

Thank u in advance

caven

---

### Post by joft on 2006-02-07
[QUOTE=caven80]can some please tell me where can i submit a NEW POST..[/QUOTE]

Go to the (sub)forum you like to post to and then chose "Forum tools". This item is at the top/header (right side) of the thread list (next to "Search this Foum"). There you can select "Post a new thread".

---

### Post by Ramses de Norre on 2006-02-07
Or click the little blue thing left above the threadlist;)

---

