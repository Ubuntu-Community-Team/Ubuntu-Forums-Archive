---
title: "Show hostname of different servers in shell tabs"
date: 2013-06-28
forum: Desktop Environments
---

### Post by patty92 on 2013-06-28
Hi all,

I have open several ssh connections to different servers in one terminal under different tabs at the same time. I just want to know what I have to do that the hostname of the different servers I am connected to, apper in the tabs of my terminal. So that I can distinguish better between the different servers. 

Regards,

patty92

---

### Post by dentaku65 on 2013-06-29
Hi,
as far as I can tell is already managed in this way in xfce4-terminal; you should have on each tabs the connected hostnames displayed, in this form:
**user@hostname**

---

### Post by steeldriver on 2013-06-29
it works that way in gnome-terminal for me as well, under the regular Ubuntu desktop - patty92, what version/flavor of Ubuntu and what terminal client (gnome-terminal? xterm? terminator?) are you using?

---

### Post by patty92 on 2013-06-29
Hi,

thank you for your answer. I guess you are right, normally this should be the case, but as you can see in my screenshot below, there are 2 tabs. The left tab is an normal terminal on my notebook and in the tab is written patty@Lenovo-G770, this is correct so far, but with the right one I am connected to my server and in the tab is also just wirtten patty@Lenovo-G770 instead of patty@fb-websrv-patty. Is there something I can put in the .bashrc maybe?

Regards,

patty

[ATTACH=CONFIG]244256[/ATTACH]

---

### Post by patty92 on 2013-06-29
Hi steeldriver,

I am using xubuntu 13.04 as operation system and my terminal client is a xfce4-terminal.

Regards,

patty

---

### Post by steeldriver on 2013-06-29
It should already be in the (default) .bashrc afaik

```

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

```

Maybe your remote ~/.bashrc is missing that part - or the $TERM environment variable isn't getting set?

---

### Post by patty92 on 2013-07-01
> **steeldriver said:**
> 

```

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

```



This is set in my  ~/.bashrc

---

### Post by dentaku65 on 2013-07-01
> **patty92 said:**
> Hi,

thank you for your answer. I guess you are right, normally this should be the case, but as you can see in my screenshot below, there are 2 tabs. The left tab is an normal terminal on my notebook and in the tab is written patty@Lenovo-G770, this is correct so far, but with the right one I am connected to my server and in the tab is also just wirtten patty@Lenovo-G770 instead of patty@fb-websrv-patty. Is there something I can put in the .bashrc maybe?

Regards,

patty

[ATTACH=CONFIG]244256[/ATTACH]

I see on your screen shot that you connecto to:
```
patty-hainer.no-ip.org
```
Is ths hostname declared somewhere on remote machine?

---

### Post by patty92 on 2013-07-05
No it is not. The hostname of the machine is "fb-websrv-patty" "patty.hainer.no-ip.org" is just the dynDNS for my server. But this issue is not only related to my own server. On my pc at work, which is running xubuntu 13.04 too the same issue appears if I connect to some servers.

---

### Post by patty92 on 2013-07-05
This entered in the ~/.bashrc works for me: 

function ssh(){
        if [ $# -lt 1 ]
        then
                echo "usage: no shh"
                return
        fi
        ssh_host=`echo $1 | cut -d "@" -f 2`
        echo -ne "\033]0;${ssh_host}"; echo -ne "\007"
        /usr/bin/ssh ${1+"$@"}
}

So this issue is solved. Thanks for all of you effort!

Regards, 

patty

---

