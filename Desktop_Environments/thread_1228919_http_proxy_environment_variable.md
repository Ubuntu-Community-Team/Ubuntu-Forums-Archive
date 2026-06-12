---
title: "http_proxy environment variable"
date: 2009-08-01
forum: Desktop Environments
---

### Post by chitresh4u on 2009-08-01
I know there are numerous posts related to this issues. But, unfortunately I am not able to get the correct environment settings even after reading and following many of the posts.

I have following lines in my ~/.bashrc

> export http_proxy=http://144.16.192.245:8080
export https_proxy=http://144.16.192.245:8080
export HTTP_PROXY=http://144.16.192.245:8080
export HTTPS_PROXY=http://144.16.192.245:8080

and following lines in /etc/environment

> http_proxy="http://144.16.192.245:8080/"
https_proxy="http://144.16.192.245:8080/"
HTTP_PROXY="http://144.16.192.245:8080/"
HTTPS_PROXY="http://144.16.192.245:8080/"

Programs started from terminal can connect to Internet without any problem. But programs started from menu are not connecting. I have rebooted after making changes to above files. But there was not change in the behavior. 

For example, checkgmail works fine when started from terminal. But when I start it from menu then it cannot connect.

What changes should be applied in order to get the correct environment setting?

---

### Post by Prospero2006 on 2009-08-01
If you are using gnome, you can go to System-Preferences-network proxy

set your proxy and apply system-wide.

?

---

### Post by chitresh4u on 2009-08-01
> **Prospero2006 said:**
> If you are using gnome, you can go to System-Preferences-network proxy

set your proxy and apply system-wide.

?

Yeah, I have done that but without any success.

---

### Post by michel.nolard on 2011-08-03
Even if the question is lying there for some time, I give my reply for anybody which would get here with some hope so that it is not deceived :

Bash's .profile, which is in your home directory is run when logging while .bashrc (in the same location) is read each time a console is open or a shell is forked.

This means that when you connect to your graphical environment using gdm/kdm/xdm/whatever, .profile only is read not .bashrc.

@chitresh4u : In your question, you said you've modified .bashrc. You now know why it's not working :-)

You've several solutions :
[LIST]
[*] add the (nearly standard) requirement to .profile to read .bashrc :
```
if [ -f ~/.bashrc ];
then
 . ~/.bashrc
fi
```

[*] or you can put your proxy configuration, directly in .profile,

[*] or you can put the proxy configuration in a script which you store in ~/bin for example, and make executable using chmod +x <scriptname> and call in ~/.profile and ~/.bashrc and even in consoles when required.

[/LIST]

You can make the script solution smarter with some minimal argument processing like this:
```
case "$1" in
 home)
  export http_proxy="http://myproxy.local.geek:8080"
  export https_proxy=$http_proxy
  export http_no_proxy="mumsPC,*.local.geek,*.example.com"
  export https_no_proxy=$http_no_proxy
 ;;

 none)
  export http_proxy=""
  export https_proxy=""
  export http_no_proxy=""
  export https_no_proxy=""
 ;;

 hotel)
  export http_proxy="..."
  export https_proxy="..."
  export http_no_proxy="..."
  export https_no_proxy="..."
 ;;
esac
```

If the script is called after your dog, and assuming ~/bin is in your path, you just call it like this if you're at home :
$ indiana home

I like very much the idea of the external script ... maybe because I actually use it myself at home and at work ;-)

---

