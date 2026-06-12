---
title: "changing command prompt...?"
date: 2008-11-02
forum: Desktop Environments
---

### Post by kcode on 2008-11-02
How can i change command prompt? I know it can be done by tweaking .bashrc
(im using bash shell), specifically by changing PS1.But im unable to decode the code.:confused:

thanks

---

### Post by malspa on 2008-11-02
I don't know how others have done it.  In Hardy the bashrc stuff looks more complicated than in some other distros.



In Hardy, I changed the user prompt to green by editing the 2nd PS1 line in this section of ~/.bashrc:

if [ "$color_prompt" = yes ]; then
    PS1="${debian_chroot:+($debian_chroot)}\e[1;31m\u[\w]\\$ \e[m  "
else
    [B]#changed the PS1 below on 6/14/08 for a color prompt
    PS1='${debian_chroot:+($debian_chroot)}\[\e[1;32m\]\u[\w]\\$ \[\e[m\]  '[/B]
fi



Also in Hardy, I changed changed the root prompt to red by editing the 2nd PS1 line in this section of /root/.bashrc:

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    [B]# changed 6/14/08 for a red root prompt
    PS1='${debian_chroot:+($debian_chroot)}\e[1;31m\u[\w]\\$ \e[m '[/B]
    ;;
esac


Good luck.  Here's the Bash Prompt HOWTO, if that helps:  [http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/index.html](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/index.html)

---

