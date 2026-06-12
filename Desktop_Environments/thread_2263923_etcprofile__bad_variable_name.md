---
title: "/etc/profile : bad variable name"
date: 2015-02-04
forum: Desktop Environments
---

### Post by benas3 on 2015-02-04
yo all. I`m having problems that i can`t log in to desktop... every time when I trying to log in my acc it always screen goes black and refresh`s back to login screen ... So I checked what`s happening it in on terminal, logged in with my acc and i wrote "cat ~/.xsession-errors" and i got that text : /usr/sbin/lightdm-session :32: export/etc/profile : bad variable name." I know that I must edit something, but [B]which file and edit to what? 

[/B]I`m new on ubuntu :D just one week

---

### Post by benas3 on 2015-02-10
up

---

### Post by steeldriver on 2015-02-10
You probably need to edit the /usr/sbin/lightdm-session file (which is a script file, not a binary executable)

I probably don't have exactly the same file as you (what version of Ubuntu are you running?) but I imagine the section in question should look something like this:

```

# Load profile
[B]for file in "/etc/profile" "$HOME/.profile" "/etc/xprofile" "$HOME/.xprofile"; do
[/B]    if [ -f "$file" ]; then
        echo "Loading profile from $file";
        . "$file"
    fi
done

```

---

### Post by benas3 on 2015-02-27
I'm using Ubuntu 14.04. Ok I'll try it, hope it helps :)


edit:


Hmmmmm... that code doesn't work for me... Firstly Gedit doesn't open file's anymore, so I'am forced to do           sudo apt-get upgrade          to fix everything, and guess what happened :) Now i was able to login to my account, but still that error show's up, so I used your code to edit via terminal which is working, and everything became back :( still can't login to my desktop, and on tty3 doesn't work gedit...

Seems I'm having huge problem :(

---

