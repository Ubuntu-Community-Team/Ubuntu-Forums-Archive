---
title: "[SOLVED] Veure pag. MAN en castellà"
date: 2008-06-03
forum: Catalan Team
---

### Post by Pablitus on 2008-06-03
Wola! Molt bones!

Per intentar aclarir-me i anar aprenent a fer servir l'ordinador estic intentant poder veure les pàgines man en castellà (en anglès em perdo la mitat d'informació). I la cosa ha anat així:

- He descarregat els paquets manpages-es i manpages-es-extra 
- Vai trobar la comanda per "cridar-les": man -M /usr/share/man/es comanda
- Vai saber que existien els alias:  alias manes="man -M /usr/share/man/es"
- On m'he quedat estancat és en fer que el bash recordi aquest alias, ja qu no tinc un fitxer anomenat ~/.bash_aliases. Cada cop que tanco la shell he de tornar a posar l'alias.

Tota la info d'aquests passos l'he tret de: [http://laventuradelpingui.blogspot.com/search/label/idiomes](http://laventuradelpingui.blogspot.com/search/label/idiomes)

No m'ha funcionat crear-la jo. He intentat afegir la línia al fitxer .bashrc de la meva home, i tampoc. He intentat aprendre anglès amb "aprenda inglés con mil palabras" i ...

Alguna idea de què és el que fai malament?
Salut i gràcies!!

Uso Ubuntu 8.04

---

### Post by Pablitus on 2008-06-03
Enganxo el què diu al .bashrc per completar la qüestió. La línia que he afegit jo és a baix de tot, i l'he pintada de vermell:

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
export HISTCONTROL=ignoreboth

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_colored_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion

[COLOR="Red"]# Man en castellà
alias manes="man -M /usr/share/man/es"
[/COLOR]
fi

---

### Post by Pablitus on 2008-06-03
Increïble, ho he tornat a provar només per enganxar al post anterior el que tenia al fitxer .bashrc (ho havia esborrat). I sí m'ha funcionat!

M'he quedat sense saber què feia malament, suposo que faltava alguna cometa o algo...

Ara quan escric *manes elquèsigui* em surt la pàgina del manual de *elquèsigui* en castellà. Iuju!!!

Fins aviat!!
Pau

---

### Post by papapep on 2008-06-03
Entenc que el que has fet entre el primer post i l'últim és tancar el terminal i tornar-lo a obrir. Les variables d'entorn i demés paràmetres del shell es carreguen quan s'inicia l'intèrpret d'ordres.

---

### Post by Pablitus on 2008-06-03
Potser només això que dius era la qüestió! I jo ho provava en la mateixa sessió del shell, i veient que no funcionava vaig esborrar el què havia afegit no fos cas que a sobre em carregués res. Ara ho he tornat a provar només per fer-vos la consulta i enganxar al post el què afegia al *.bashrc* i echo! Functiona!!

Gràcies! "nunca a la cama te irás sin saber una cosa más".

---

