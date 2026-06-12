---
title: "weird &quot;set&quot; output?"
date: 2006-06-15
forum: Desktop Environments
---

### Post by Cantabile on 2006-06-15
Hi, I recently reinstalled Dapper on my laptop. All was well until I noticed that the "set" command gives more than just some environment variables, the output is like this:

> 
........
(more environ variables here)
XMODIFIERS=@im=SCIM
_=--color=auto
bash205='3.1.17(1)-release'
bash205b='3.1.17(1)-release'
bash3='3.1.17(1)-release'
_alias ()
{
    local cur;
    COMPREPLY=();
    cur=${COMP_WORDS[$COMP_CWORD]};
    case "$COMP_LINE" in
        *[^=])
            COMPREPLY=($( compgen -A alias -S '=' -- $cur ))
        ;;
        *=)
            COMPREPLY=("$( alias ${cur%=} 2>/dev/null |                              sed -e 's|^alias '$cur'\(.*\)$|\1|' )")
        ;;
    esac
}
_apt_cache ()
{
    local cur prev special i;
    COMPREPLY=();
    cur=${COMP_WORDS[COMP_CWORD]};
    prev=${COMP_WORDS[COMP_CWORD-1]};
    if [ "$cur" != show ]; then
        for ((i=0; i < ${#COMP_WORDS[@]}-1; i++ ))
        do
            if [[ ${COMP_WORDS[i]} == @(add|depends|dotty|policy|rdepends|show?(pkg|src|)) ]]; then
                special=${COMP_WORDS[i]};
            fi;
        done;
    fi;
..........
(more funny output here)


It seems "set" is trying to print out some script(?), which I had never seen on other distributions. Anybody get any idea about how could this happen? It's not a big deal, but I still want to get it straight. BTW, I'm using bash. Thanks in advance.

---

### Post by Cantabile on 2006-06-19
Anybody has similar problem? Also could anybody help check whether set gives similar results under 5.10? I definitely will not switch back but just want to know:roll:
Cheers.

---

