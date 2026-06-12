---
title: "Set Output Error"
date: 2007-12-01
forum: Desktop Environments
---

### Post by firestarsolo on 2007-12-01
Hello, I just recently installed Ubuntu 7.10, and when I type the "set" command into a terminal, here's what I get:

```
BASH=/bin/bash

BASH_ARGC=()

BASH_ARGV=()

BASH_COMPLETION=/etc/bash_completion

BASH_COMPLETION_DIR=/etc/bash_completion.d

BASH_LINENO=()

BASH_SOURCE=()

BASH_VERSINFO=([0]="3" [1]="2" [2]="25" [3]="1" [4]="release" [5]="i486-pc-linux-gnu")

BASH_VERSION='3.2.25(1)-release'

COLORTERM=gnome-terminal

COLUMNS=80

DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-3IERTerXOR,guid=5e9df28164ad2d19c3e9860047519cd0

DESKTOP_SESSION=default

DIRSTACK=()

DISPLAY=:0.0

EUID=1000

GDMSESSION=default

GDM_LANG=en_US.UTF-8

GDM_XSERVER_LOCATION=local

GNOME_DESKTOP_SESSION_ID=Default

GNOME_KEYRING_PID=5475

GNOME_KEYRING_SOCKET=/tmp/keyring-XPASnx/socket

GROUPS=()

GTK_RC_FILES=/etc/gtk/gtkrc:/home/firestarsolo/.gtkrc-1.2-gnome2

HISTCONTROL=ignoreboth

HISTFILE=/home/firestarsolo/.bash_history

HISTFILESIZE=500

HISTSIZE=500

HOME=/home/firestarsolo

HOSTNAME=ubuntu

HOSTTYPE=i486

IFS=$' \t\n'

LANG=en_US.UTF-8

LESSCLOSE='/usr/bin/lesspipe %s %s'

LESSOPEN='| /usr/bin/lesspipe %s'

LIBGL_DRIVERS_PATH=/usr/lib/dri

LINES=24

LOGNAME=firestarsolo

LS_COLORS='no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:'

MACHTYPE=i486-pc-linux-gnu

MAILCHECK=60

OLDPWD=/home/firestarsolo

OPTERR=1

OPTIND=1

OSTYPE=linux-gnu

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

PIPESTATUS=([0]="0")

PPID=31297

PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'

PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

PS2='> '

PS4='+ '

PWD=/home/firestarsolo/OS/lab5

SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/5478

SHELL=/bin/bash

SHELLOPTS=braceexpand:emacs:hashall:histexpand:interactive-comments:monitor

SHLVL=1

SSH_AGENT_PID=5513

SSH_AUTH_SOCK=/tmp/ssh-MJueWO5478/agent.5478

TERM=xterm

UID=1000

USER=firestarsolo

USERNAME=firestarsolo

WINDOWID=48234592

WINDOWPATH=7

XAUTHORITY=/home/firestarsolo/.Xauthority

XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/

XDG_SESSION_COOKIE=27e5316c5ab65263a5a12c0047507700-1196530894.736243-604043003

_=declare

bash205='3.2.25(1)-release'

bash205b='3.2.25(1)-release'

bash3='3.2.25(1)-release'

t=yes

test=yes

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

            COMPREPLY=("$( alias ${cur%=} 2>/dev/null | 			     sed -e 's|^alias '$cur'\(.*\)$|\1|' )")

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

            if [[ ${COMP_WORDS[i]} == @(add|depends|dotty|policy|rdepends|madison|show?(pkg|src|)) ]]; then

                special=${COMP_WORDS[i]};

            fi;

        done;

    fi;

    if [ -n "$special" ]; then

        case $special in 

            add)

                _filedir;

                return 0

            ;;

            *)

                COMPREPLY=($( apt-cache pkgnames $cur 2> /dev/null ));

                return 0

            ;;

        esac;

    fi;

    case "$prev" in 

        -@(c|p|s|-config-file|-@(pkg|src)-cache))

            _filedir;

            return 0

        ;;

        search)

            if [[ "$cur" != -* ]]; then

                return 0;

            fi

        ;;

    esac;

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( compgen -W '-h -v -p -s -q -i -f -a -g -c \

				-o --help --version --pkg-cache --src-cache \

				--quiet --important --full --all-versions \

				--no-all-versions --generate --no-generate \

				--names-only --all-names --recurse \

				--config-file --option' -- $cur ));

    else

        COMPREPLY=($( compgen -W 'add gencaches show showpkg showsrc \

				stats dump dumpavail unmet search search \

				depends rdepends pkgnames dotty xvcg \

				policy madison' -- $cur ));

    fi;

    return 0

}

_apt_get () 

{ 

    local cur prev special i;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    for ((i=0; i < ${#COMP_WORDS[@]}-1; i++ ))

    do

        if [[ ${COMP_WORDS[i]} == @(install|remove|source|build-dep) ]]; then

            special=${COMP_WORDS[i]};

        fi;

    done;

    if [ -n "$special" ]; then

        case $special in 

            remove)

                if [ -f /etc/debian_version ]; then

                    COMPREPLY=($( _comp_dpkg_installed_packages 						$cur ));

                else

                    _rpm_installed_packages;

                fi;

                return 0

            ;;

            *)

                COMPREPLY=($( apt-cache pkgnames $cur 2> /dev/null ));

                return 0

            ;;

        esac;

    fi;

    case "$prev" in 

        -@(c|-config-file))

            _filedir;

            return 0

        ;;

        -@(t|-target-release|-default-release))

            COMPREPLY=($( apt-cache policy | 				    grep "release.o=Debian,a=$cur" | 				    sed -e "s/.*a=\(\w*\).*/\1/" | uniq 2> /dev/null));

            return 0

        ;;

    esac;

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( compgen -W '-d -f -h -v -m -q -s -y \

				-u -t -b -c -o --download-only --fix-broken \

				--help --version --ignore-missing \

				--fix-missing --no-download --quiet --simulate \

				--just-print --dry-run --recon --no-act --yes \

				--assume-yes --show-upgraded --only-source \

				--compile --build --ignore-hold \

				--target-release --no-upgrade --force-yes \

				--print-uris --purge --reinstall \

				--list-cleanup --default-release \

				--trivial-only --no-remove --diff-only \

				--tar-only --config-file --option' -- $cur ));

    else

        COMPREPLY=($( compgen -W 'update upgrade dselect-upgrade \

				dist-upgrade install remove source build-dep \

				check clean autoclean autoremove' -- $cur ));

    fi;

    return 0

}

_aptitude () 

{ 

    local cur dashoptions prev special i;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    dashoptions='-S -u -i -h --help --version -s --simulate -d \

		     --download-only -P --prompt -y --assume-yes -F \

		     --display-format -O --sort -w --width -f -r -g \

		     --with-recommends --with-suggests -R -G \

		     --without-recommends --without-suggests -t \

		     --target-release -V --show-versions -D --show-deps\

		     -Z -v --verbose';

    for ((i=0; i < ${#COMP_WORDS[@]}-1; i++ ))

    do

        if [[ ${COMP_WORDS[i]} == @(install|reinstall|hold|unhold|markauto|unmarkauto|dist-upgrade|full-upgrade|download|show|forbid-version|purge|remove|changelog|why|why-not|keep|keep-all) ]]; then

            special=${COMP_WORDS[i]};

        fi;

        [[ ${COMP_WORDS[i]} == '-u' ]] && dashoptions=${dashoptions/-i};

        [[ ${COMP_WORDS[i]} == '-i' ]] && dashoptions=${dashoptions/-u};

    done;

    if [[ -n "$special" ]]; then

        case $special in 

            @(install|hold|markauto|unmarkauto|dist-upgrade|full-upgrade|download|show|changelog|why|why-not))

                COMPREPLY=($( apt-cache pkgnames $cur 2> /dev/null ));

                return 0

            ;;

            @(purge|remove|reinstall|forbid-version))

                COMPREPLY=($( _comp_dpkg_installed_packages $cur ));

                return 0

            ;;

            unhold)

                COMPREPLY=($( _comp_dpkg_hold_packages $cur ));

                return 0

            ;;

        esac;

    fi;

    case $prev in 

        @(autoclean|clean|forget-new|search|upgrade|safe-upgrade|update|keep-all))

            return 0

        ;;

        -S)

            _filedir;

            return 0

        ;;

        -@(t|-target-release|-default-release))

            COMPREPLY=($( apt-cache policy | 		    grep "release.o=Debian,a=$cur" | 		    sed -e "s/.*a=\(\w*\).*/\1/" | uniq 2> /dev/null ));

            return 0

        ;;

    esac;

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( compgen -W "$dashoptions" -- $cur ));

    else

        COMPREPLY=($( compgen -W 'update upgrade safe-upgrade forget-new clean \

				       autoclean install reinstall remove \

				       hold unhold purge markauto unmarkauto why why-not \

				       dist-upgrade full-upgrade download search show \

				       forbid-version changelog keep-all' -- $cur ));

    fi;

    return 0

}

_aspell () 

{ 

    local cur prev;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case "$prev" in 

        @(-c|-p|check))

            _filedir;

            return 0

        ;;

        @(dump|create|merge))

            COMPREPLY=($( compgen -W 'master personal repl' -- $cur ));

            return 0

        ;;

        -d)

            _aspell_dictionary;

            return 0

        ;;

    esac;

    if [[ "$cur" == *=* ]]; then

        prev=${cur/=*/};

        cur=${cur/*=/};

        case "$prev" in 

            --@(conf|personal|repl|per-conf))

                _filedir;

                return 0

            ;;

            --@(conf-dir|data-dir|dict-dir|home-dir|local-data-dir|prefix))

                _filedir -d;

                return 0

            ;;

            --master)

                _aspell_dictionary;

                return 0

            ;;

            --mode)

                COMPREPLY=($( compgen -W 'none url email sgml tex' -- $cur ));

                return 0

            ;;

            --sug-mode)

                COMPREPLY=($( compgen -W 'ultra fast normal bad-speller' -- $cur ));

                return 0

            ;;

            --keymapping)

                COMPREPLY=($( compgen -W 'aspell ispell' -- $cur ));

                return 0

            ;;

        esac;

    fi;

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( compgen -W '--conf= --conf-dir= --data-dir= --dict-dir= \

			--encoding= --add-filter= --rem-filter= --mode= -e \

			-H -t --add-extra-dicts= --rem-extra-dicts= \

			--home-dir= -W --ignore= --ignore-accents \

			--dont-ignore-accents --ignore-case --dont-ignore-case \

			--ignore-repl --dont-ignore-repl --jargon= --keyboard= \

			--lang= --language-tag= --local-data-dir= -d --master= \

			--module= --add-module-search-order= \

			--rem-module-search-order= --per-conf= -p --personal= \

			--prefix= --repl= -C -B --run-together --dont-run-together \

			--run-together-limit= --run-together-min= --save-repl \

			--dont-save-repl --set-prefix --dont-set-prefix --size= \

			--spelling= --strip-accents --dont-strip-accents \

			--sug-mode= --add-word-list-path= --rem-word-list-path= \

			-b -x --backup -b|-x --dont-backup --reverse --dont-reverse \

			--time --dont-time --keymapping= --add-email-quote= \

			--rem-email-quote= --email-margin= --add-tex-command= \

			--rem-tex-command= --tex-check-comments \

			--dont-tex-check-comments --add-tex-extension= \

			--rem-tex-extension= --add-sgml-check= --rem-sgml-check= \

			--add-sgml-extension= --rem-sgml-extension=' -- $cur ));

    else

        COMPREPLY=($( compgen -W '-? help -c check -a pipe -l list \

			config config soundslike filter -v version dump \

			create merge' -- $cur ));

    fi

}

_aspell_dictionary () 

{ 

    local datadir;

    datadir=/usr/lib/aspell;

    COMPREPLY=($( command ls $datadir/*.@(multi|alias) ));

    COMPREPLY=(${COMPREPLY[@]%.@(multi|alias)});

    COMPREPLY=($( compgen -W '${COMPREPLY[@]#$datadir/}' -- $cur ))

}

_available_interfaces () 

{ 

    local cmd;

    if [ "${1:-}" = -w ]; then

        cmd="iwconfig";

    else

        if [ "${1:-}" = -a ]; then

            cmd="ifconfig";

        else

            cmd="ifconfig -a";

        fi;

    fi;

    COMPREPLY=($( eval $cmd 2>/dev/null | 		sed -ne 's|^\('$cur'[^[:space:][:punct:]]\{1,\}\).*$|\1|p'))

}

_bzip2 () 

{ 

    local cur prev xspec IFS='	

';

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( compgen -W '-c -d -f -h -k -L -q -s \

			-t -v -V -z -1 -2 -3 -4 -5 -6 -7 -8 -9 \

			--help --decompress --compress --keep --force \

			--test --stdout --quiet --verbose --license \

			--version --small --fast --best' -- $cur ));

        return 0;

    fi;

    xspec="*.bz2";

    if [[ "$prev" == --* ]]; then

        [[ "$prev" == --decompress || "$prev" == --list || "$prev" == --test ]] && xspec="!"$xspec;

        [[ "$prev" == --compress ]] && xspec=;

    else

        if [[ "$prev" == -* ]]; then

            [[ "$prev" == -*[dt]* ]] && xspec="!"$xspec;

            [[ "$prev" == -*z* ]] && xspec=;

        fi;

    fi;

    _expand || return 0;

    COMPREPLY=($( compgen -f -X "$xspec" -- $cur ) $( compgen -d -- $cur ))

}

_cancel () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    COMPREPLY=($( lpstat | cut -d' ' -f1 | grep "^$cur" ))

}

_cd () 

{ 

    local IFS='	

' cur=${COMP_WORDS[COMP_CWORD]} i j k;

    if [[ "$cur" == ?(\\)\$* ]]; then

        COMPREPLY=($( compgen -v -P '$' -- "${cur#?(\\)$}" ));

        return 0;

    fi;

    if [ -z "${CDPATH:-}" ] || [[ "$cur" == ?(.)?(.)/* ]]; then

        _filedir -d;

        return 0;

    fi;

    local -r mark_dirs=$(_rl_enabled mark-directories && echo y);

    local -r mark_symdirs=$(_rl_enabled mark-symlinked-directories && echo y);

    for i in ${CDPATH//:/'	'};

    do

        k=${#COMPREPLY[@]};

        for j in $( compgen -d $i/$cur );

        do

            if [[ ( -n $mark_symdirs && -h $j || -n $mark_dirs && ! -h $j ) && ! -d ${j#$i/} ]]; then

                j="${j}/";

            fi;

            COMPREPLY[k++]=${j#$i/};

        done;

    done;

    _filedir -d;

    if [[ ${#COMPREPLY[@]} -eq 1 ]]; then

        i=${COMPREPLY[0]};

        if [ "$i" == "$cur" ] && [[ $i != "*/" ]]; then

            COMPREPLY[0]="${i}/";

        fi;

    fi;

    return 0

}

_chgrp () 

{ 

    local cur prev;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    cur=${cur//\\\\/};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( compgen -W '-c -h -f -R -v --changes \

		--dereference --no-dereference --silent --quiet \

		--reference= --recursive --verbose --help --version' -- $cur ));

        return 0;

    fi;

    if [ $COMP_CWORD -eq 1 ] && [[ "$cur" != -* ]] || [[ "$prev" == -* ]] && [ -n "$bash205" ]; then

        local IFS='

';

        COMPREPLY=($( compgen -g $cur 2>/dev/null ));

    else

        _filedir || return 0;

    fi;

    return 0

}

_chown () 

{ 

    local cur;

    cur=${COMP_WORDS[COMP_CWORD]};

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( compgen -W '-c -h -f -R -v --changes \

		--dereference --no-dereference --from= --silent --quiet \

		--reference= --recursive --verbose --help --version' -- $cur ));

    else

        _count_args;

        case $args in 

            1)

                _usergroup

            ;;

            *)

                _filedir

            ;;

        esac;

    fi

}

_chsh () 

{ 

    local cur prev;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    if [ "$prev" = "-s" ]; then

        if [ -f /etc/debian_version ]; then

            COMPREPLY=($( </etc/shells ));

        else

            COMPREPLY=($( chsh -l | grep "^$cur" ));

        fi;

    else

        COMPREPLY=($( compgen -u -- $cur ));

    fi;

    return 0

}

_command () 

{ 

    local cur func cline cspec noglob cmd done i _COMMAND_FUNC _COMMAND_FUNC_ARGS;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    done=;

    while [ -z $done ]; do

        cmd=${COMP_WORDS[1]};

        if [[ "$cmd" == -* ]]; then

            for ((i=1 ; i<=COMP_CWORD ; i++))

            do

                COMP_WORDS[i]=${COMP_WORDS[i+1]};

            done;

            COMP_CWORD=$(($COMP_CWORD-1));

        else

            done=1;

        fi;

    done;

    if [ $COMP_CWORD -eq 1 ]; then

        COMPREPLY=($( compgen -c -- $cur ));

    else

        if complete -p $cmd >&/dev/null; then

            cspec=$( complete -p $cmd );

            if [ "${cspec#* -F }" != "$cspec" ]; then

                COMP_CWORD=$(( $COMP_CWORD - 1 ));

                func=${cspec#*-F };

                func=${func%% *};

                cline="${COMP_LINE#*( )$1 }";

                shopt -qo noglob;

                noglob=$?;

                shopt -so noglob;

                COMP_WORDS=($cline);

                [ $noglob -eq 1 ] && shopt -uo noglob;

                $func $cline;

                COMP_CWORD=$(( $COMP_CWORD > 0 ? $COMP_CWORD : 1 ));

                cur=${COMP_WORDS[COMP_CWORD]};

                _COMMAND_FUNC=$func;

                _COMMAND_FUNC_ARGS=($cmd $2 $3);

                COMP_LINE=$cline;

                COMP_POINT=$(( ${COMP_POINT} - ${#1} - 1 ));

                $func $cmd $2 $3;

                if [ "${cspec#*-o }" != "$cspec" ]; then

                    cspec=${cspec#*-o };

                    cspec=${cspec%% *};

                    if [[ "$cspec" != @(dir|file)names ]]; then

                        COMPREPLY=("${COMPREPLY[@]//\\\\:/:}");

                    fi;

                fi;

            else

                if [ -n "$cspec" ]; then

                    cspec=${cspec#complete};

                    cspec=${cspec%%$cmd};

                    COMPREPLY=($( eval compgen "$cspec" -- "$cur" ));

                fi;

            fi;

        fi;

    fi;

    [ ${#COMPREPLY[@]} -eq 0 ] && _filedir

}

_comp_dpkg_hold_packages () 

{ 

    grep -B 2 'hold' /var/lib/dpkg/status | grep "Package: $1" | cut -d\  -f2

}

_comp_dpkg_installed_packages () 

{ 

    grep -A 2 "Package: $1" /var/lib/dpkg/status | grep -B 2 'ok installed' | grep "Package: $1" | cut -d\  -f2

}

_complete () 

{ 

    local cur prev options;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case $prev in 

        -o)

            options="default dirnames filenames";

            [ -n "$bash205b" ] && options="$options nospace";

            [ -n "$bash3" ] && options="$options bashdefault plusdirs";

            COMPREPLY=($( compgen -W "$options" -- $cur ));

            return 0

        ;;

        -A)

            COMPREPLY=($( compgen -W 'alias arrayvar binding \

				builtin command directory disabled enabled \

				export file function group helptopic hostname \

				job keyword running service setopt shopt \

				signal stopped user variable' -- $cur ));

            return 0

        ;;

        -C)

            COMPREPLY=($( compgen -A command -- $cur ));

            return 0

        ;;

        -F)

            COMPREPLY=($( compgen -A function -- $cur ));

            return 0

        ;;

        -@(p|r))

            COMPREPLY=($( complete -p | sed -e 's|.* ||' | 					grep "^$cur" ));

            return 0

        ;;

    esac;

    if [[ "$cur" == -* ]]; then

        options="-a -b -c -d -e -f -g -j -k -s -v -u -A -G -W -P -S -X -F -C";

        [ -n "$bash205" ] && options="$options -o";

        COMPREPLY=($( compgen -W "$options" -- $cur ));

    else

        COMPREPLY=($( compgen -A command -- $cur ));

    fi

}

_configure_func () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    [[ "$cur" != -* ]] && return 0;

    if [ -n "$COMP_CONFIGURE_HINTS" ]; then

        COMPREPLY=($( $1 --help | awk '/^  --[A-Za-z]/ { print $1; if ($2 ~ /--[A-Za-z]/) print $2 }' | sed -e 's/[[,].*//g' | grep ^$cur ));

    else

        COMPREPLY=($( $1 --help | awk '/^  --[A-Za-z]/ { print $1; if ($2 ~ /--[A-Za-z]/) print $2 }' | sed -e 's/[[,=].*//g' | grep ^$cur ));

    fi

}

_configured_interfaces () 

{ 

    if [ -f /etc/debian_version ]; then

        COMPREPLY=($( sed -ne 's|^iface \([^ ]\+\).*$|\1|p' 			       /etc/network/interfaces ));

    else

        if [ -f /etc/SuSE-release ]; then

            COMPREPLY=($( command ls 			/etc/sysconfig/network/ifcfg-* | 			sed -ne 's|.*ifcfg-\('$cur'.*\)|\1|p' ));

        else

            if [ -f /etc/pld-release ]; then

                COMPREPLY=($( command ls -B 			/etc/sysconfig/interfaces | 			sed -ne 's|.*ifcfg-\('$cur'.*\)|\1|p' ));

            else

                COMPREPLY=($( command ls 			/etc/sysconfig/network-scripts/ifcfg-* | 			sed -ne 's|.*ifcfg-\('$cur'.*\)|\1|p' ));

            fi;

        fi;

    fi

}

_count_args () 

{ 

    args=1;

    for ((i=1; i < COMP_CWORD; i++ ))

    do

        if [[ "${COMP_WORDS[i]}" != -* ]]; then

            args=$(($args+1));

        fi;

    done

}

_cpio () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case $prev in 

        -H)

            _cpio_format;

            return 0

        ;;

        -@(E|F|I))

            _filedir;

            return 0

        ;;

        -R)

            _usergroup;

            return 0

        ;;

    esac;

    if [[ "$cur" == *=* ]]; then

        prev=${cur/=*/};

        cur=${cur/*=/};

        case $prev in 

            --format)

                _cpio_format;

                return 0

            ;;

            --@(file|pattern-file))

                _filedir;

                return 0

            ;;

            --owner)

                _usergroup;

                return 0

            ;;

            --rsh-command)

                COMPREPLY=($( compgen -c -- $cur ));

                return 0

            ;;

        esac;

    fi;

    if [ $COMP_CWORD -eq 1 ]; then

        COMPREPLY=($( compgen -W '-o --create -i --extract -p --pass-through' -- $cur));

    else

        case ${COMP_WORDS[1]} in 

            -@(o|-create))

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-0 -a -c -v -A -B\

						-L -V -C -H -M -O -F --file= --format=\

						--message= --null --reset-access-time\

						--verbose --dot --append --block-size=\

						--dereference --io-size= --quiet\

						--force-local --rsh-command= --help\

						--version' -- $cur ));

                fi

            ;;

            -@(i|-extract))

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-b -c -d -f -m -n -r\

						-t -s -u -v -B -S -V -C -E -H -M -R -I\

						-F --file= --make-directories\

						--nonmatching\

						--preserve-modification-time\

						--numeric-uid-gid --rename -t --list\

						--swap-bytes --swap --dot\

						--unconditional --verbose --block-size=\

						--swap-halfwords --io-size=\

						--pattern-file= --format= --owner=\

						--no-preserve-owner --message=\

						--force-local --no-absolute-filenames\

						--sparse --only-verify-crc --quiet\

						--rsh-command= --help\

						--version' -- $cur ));

                fi

            ;;

            -@(p|-pass-through))

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-0 -a -d -l -m -u -v\

						-L -V -R --null --reset-access-time\

						--make-directories --link --quiet\

						--preserve-modification-time\

						--unconditional --verbose --dot\

						--dereference --owner=\

						--no-preserve-owner --sparse --help\

						--version' -- $cur ));

                else

                    _filedir -d;

                fi

            ;;

        esac;

    fi

}

_cpio_format () 

{ 

    COMPREPLY=($( compgen -W 'bin odc newc crc tar ustar hpbin hpodc' -- $cur ))

}

_dd () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    case "$cur" in 

        if=* | of=*)

            cur=${cur#*=};

            _filedir;

            return 0

        ;;

        conv=*)

            cur=${cur#*=};

            COMPREPLY=($( compgen -W 'ascii ebcdic ibm block unblock \

				lcase notrunc ucase swab noerror sync' 				-- $cur ));

            return 0

        ;;

    esac;

    _expand || return 0;

    COMPREPLY=($( compgen -W '--help --version' -- $cur ) $( compgen -W 'bs cbs conv count ibs if obs of seek skip'				-S '=' -- $cur ))

}

_debconf_show () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    COMPREPLY=($( compgen -W '--listowners --listdbs --db=' -- $cur ) $( apt-cache pkgnames -- $cur ))

}

_dhclient () 

{ 

    local cur prev;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case "$prev" in 

        -@(cf|lf|pf|sf))

            _filedir;

            return 0

        ;;

        -s)

            _known_hosts;

            return 0

        ;;

    esac;

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( compgen -W '-p -d -q -1 -r -lf -pf \

			-cf -sf -s -g -n -nw -w' -- $cur ));

    else

        _available_interfaces;

    fi

}

_dpkg () 

{ 

    local cur prev i;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    i=$COMP_CWORD;

    _expand || return 0;

    if [[ $cur != -* ]]; then

        while [[ $prev != -* && $i != 1 ]]; do

            i=$((i-1));

            prev=${COMP_WORDS[i-1]};

        done;

    fi;

    case "$prev" in 

        -@(c|i|A|I|f|e|x|X|-@(install|unpack|record-avail|contents|info| 			  fsys-tarfile|field|control|extract)))

            _filedir '?(u)deb';

            return 0

        ;;

        -@(b|-build))

            _filedir -d;

            return 0

        ;;

        -@(s|p|l|-@(status|print-avail|list)))

            COMPREPLY=($( apt-cache pkgnames $cur 2>/dev/null ));

            return 0

        ;;

        -@(S|-search))

            _filedir;

            return 0

        ;;

        -@(r|L|P|-@(remove|purge|listfiles)))

            COMPREPLY=($( _comp_dpkg_installed_packages $cur ));

            return 0

        ;;

        *)

            COMPREPLY=($( compgen -W '-i --install --unpack -A --record-avail \

			--configure -r --remove -P --purge --get-selections \

			--set-selections --update-avail --merge-avail \

			--clear-avail  --command-fd --forget-old-unavail -s \

			--status -p --print-avail -L --listfiles -l --list \

			-S --search -C --audit --print-architecture \

			--print-gnu-build-architecture \

			--print-installation-architecture \

			--compare-versions --help --version --force-help \

			--force-all --force-auto-select --force-downgrade \

			--force-configure-any --force-hold --force-bad-path \

			--force-not-root --force-overwrite \

			--force-overwrite-diverted --force-bad-verify \

			--force-depends-version --force-depends \

			--force-confnew --force-confold --force-confdef \

			--force-confmiss --force-conflicts --force-architecture\

			--force-overwrite-dir --force-remove-reinstreq \

			--force-remove-essential -Dh \

			--debug=help --licence --admindir= --root= --instdir= \

			-O --selected-only -E --skip-same-version \

			-G --refuse-downgrade -B --auto-deconfigure \

			--no-debsig --no-act -D --debug= --status-fd \

			-b --build -I --info -f --field -c --contents \

			-x --extract -X --vextract --fsys-tarfile -e --control \

			--ignore-depends= --abort-after' -- $cur ))

        ;;

    esac

}

_dpkg_reconfigure () 

{ 

    local cur prev opt;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case "$prev" in 

        -@(f|-frontend))

            opt=($( echo /usr/share/perl5/Debconf/FrontEnd/* ));

            opt=(${opt[@]##*/});

            opt=(${opt[@]%.pm});

            COMPREPLY=($( compgen -W '${opt[@]}' -- $cur ));

            return 0

        ;;

        -@(p|-priority))

            COMPREPLY=($( compgen -W 'low medium high critical' -- $cur ));

            return 0

        ;;

    esac;

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( compgen -W '-f --frontend -p --priority -a --all \

				       -u --unseen-only -h --help -s --showold \

				       --force --terse' -- $cur ));

    else

        COMPREPLY=($( _comp_dpkg_installed_packages $cur ));

    fi

}

_expand () 

{ 

    [ "$cur" != "${cur%\\}" ] && cur="$cur\\";

    if [[ "$cur" == \~*/* ]]; then

        eval cur=$cur;

    else

        if [[ "$cur" == \~* ]]; then

            cur=${cur#\~};

            COMPREPLY=($( compgen -P '~' -u $cur ));

            return ${#COMPREPLY[@]};

        fi;

    fi

}

_export () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[$COMP_CWORD]};

    case "$COMP_LINE" in 

        *=\$*)

            COMPREPLY=($( compgen -v -P '$' -- ${cur#*=\$} ))

        ;;

        *[^=])

            COMPREPLY=($( compgen -v -S '=' -- $cur ))

        ;;

        *=)

            COMPREPLY=("$( eval echo -n \"$`echo ${cur%=}`\" |

			( echo -n \'

			  sed -e 's/'\''/'\''\\\'\'''\''/g'

			  echo -n \' ) )")

        ;;

    esac

}

_filedir () 

{ 

    local IFS='	

' xspec;

    _expand || return 0;

    if [ "${1:-}" = -d ]; then

        COMPREPLY=(${COMPREPLY[@]:-} $( compgen -d -- $cur ));

        return 0;

    fi;

    xspec=${1:+"!*.$1"};

    COMPREPLY=(${COMPREPLY[@]:-} $( compgen -f -X "$xspec" -- "$cur" ) $( compgen -d -- "$cur" ))

}

_filedir_xspec () 

{ 

    local IFS cur xspec;

    IFS='	

';

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    _expand || return 0;

    xspec=$( sed -ne '/^complete .*[ 	]'${1##*/}'\([ 	]\|$\)/{p;q;}' 		  $BASH_COMPLETION );

    xspec=${xspec#*-X };

    xspec=${xspec%% *};

    COMPREPLY=($( eval compgen -f -X "$xspec" -- 		    \"${cur#[\`\"\']}\" 2>/dev/null ) $( compgen -d -- $cur ))

}

_find () 

{ 

    local cur prev i exprfound onlyonce;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case "$prev" in 

        -@(max|min)depth)

            COMPREPLY=($( compgen -W '0 1 2 3 4 5 6 7 8 9' -- $cur ));

            return 0

        ;;

        -?(a|c)newer | -fls | -fprint?(0|f) | -?(i)?(l)name)

            _filedir;

            return 0

        ;;

        -fstype)

            [ -e /proc/filesystems ] && COMPREPLY=($( cut -d'	' -f 2 /proc/filesystems | 				grep "^$cur" ));

            return 0

        ;;

        -gid)

            _gids;

            return 0

        ;;

        -group)

            if [ -n "$bash205" ]; then

                COMPREPLY=($( compgen -g -- $cur 2>/dev/null));

            fi;

            return 0

        ;;

        -?(x)type)

            COMPREPLY=($( compgen -W 'b c d p f l s' -- $cur ));

            return 0

        ;;

        -uid)

            _uids;

            return 0

        ;;

        -user)

            COMPREPLY=($( compgen -u -- $cur ));

            return 0

        ;;

        -exec | -ok)

            COMP_WORDS=(COMP_WORDS[0] $cur);

            COMP_CWORD=1;

            _command;

            return 0

        ;;

        -[acm]min | -[acm]time | -?(i)?(l)name | -inum | -?(i)path | -?(i)regex | -links | -perm | -size | -used | -printf)

            return 0

        ;;

    esac;

    _expand || return 0;

    for i in ${COMP_WORDS[@]};

    do

        [[ "$i" = [-\(\),\!]* ]] && exprfound=1 && break;

    done;

    if [ "$exprfound" != 1 ] && [[ "$cur" != [-\(\),\!]* ]]; then

        _filedir -d;

        return 0;

    fi;

    COMPREPLY=($( compgen -W '-daystart -depth -follow -help -maxdepth \

			-mindepth -mount -noleaf -version -xdev -amin -anewer \

			-atime -cmin -cnewer -ctime -empty -false -fstype \

			-gid -group -ilname -iname -inum -ipath -iregex \

			-links -lname -mmin -mtime -name -newer -nouser \

			-nogroup -perm -regex -size -true -type -uid -used \

			-user -xtype -exec -fls -fprint -fprint0 -fprintf -ok \

			-print -print0 -printf -prune -ls' -- $cur ));

    onlyonce=' -daystart -depth -follow -help -maxdepth -mindepth -mount \

		   -noleaf -version -xdev ';

    COMPREPLY=($( echo "${COMP_WORDS[@]}" | 		       (while read -d ' ' i; do

			    [ "$i" == "" ] ||

			    [ "${onlyonce/ ${i%% *} / }" == "$onlyonce" ] &&

			    continue

			    # flatten array with spaces on either side,

			    # otherwise we cannot grep on word boundaries of

			    # first and last word

			    COMPREPLY=" ${COMPREPLY[@]} "

			    # remove word from list of completions

			    COMPREPLY=( ${COMPREPLY/ ${i%% *} / } )

			done

			echo ${COMPREPLY[@]})

		  ));

    _filedir;

    return 0

}

_function () 

{ 

    local cur prev;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    if [[ $1 == @(declare|typeset) ]]; then

        if [ "$prev" = -f ]; then

            COMPREPLY=($( compgen -A function -- $cur ));

        else

            if [[ "$cur" == -* ]]; then

                COMPREPLY=($( compgen -W '-a -f -F -i -r -x -p' -- 				       $cur ));

            fi;

        fi;

    else

        if [ $COMP_CWORD -eq 1 ]; then

            COMPREPLY=($( compgen -A function -- $cur ));

        else

            COMPREPLY=("() $( type -- ${COMP_WORDS[1]} | sed -e 1,2d )");

        fi;

    fi

}

_gcc () 

{ 

    local cur cc backend;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    _expand || return 0;

    case "$1" in 

        gcj)

            backend=jc1

        ;;

        gpc)

            backend=gpc1

        ;;

        *77)

            backend=f771

        ;;

        *)

            backend=cc1

        ;;

    esac;

    if [[ "$cur" == -* ]]; then

        cc=$( $1 -print-prog-name=$backend );

        COMPREPLY=($( $cc --help 2>/dev/null | tr '\t' ' ' | 			       sed -e '/^  *-/!d' -e 's/ *-\([^ ]*\).*/-\1/' | 			       command grep "^$cur" | sort -u ));

    else

        _filedir;

    fi

}

_gdb () 

{ 

    local cur prev;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    if [ $COMP_CWORD -eq 1 ]; then

        COMPREPLY=($( compgen -c -- $cur ));

    else

        if [ $COMP_CWORD -eq 2 ]; then

            prev=${prev##*/};

            COMPREPLY=($( compgen -fW "$( command ps axo comm,pid | 				awk '{if ($1 ~ /^'"$prev"'/) print $2}' ) )" 				-- "$cur" ));

        fi;

    fi

}

_getent () 

{ 

    local cur prev;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case $prev in 

        passwd)

            COMPREPLY=($( compgen -u $cur  ));

            return 0

        ;;

        group)

            COMPREPLY=($( compgen -g $cur  ));

            return 0

        ;;

        services)

            COMPREPLY=($( compgen -s $cur  ));

            return 0

        ;;

        hosts)

            COMPREPLY=($( compgen -A hostname $cur  ));

            return 0

        ;;

        protocols)

            COMPREPLY=($( getent protocols | awk '{print $1}' | grep "^$cur" ));

            return 0

        ;;

        networks)

            COMPREPLY=($( getent networks | awk '{print $1}' | grep "^$cur" ));

            return 0

        ;;

    esac;

    if [ $COMP_CWORD -eq 1 ]; then

        COMPREPLY=($( compgen -W 'passwd group hosts services protocols networks' -- $cur ));

    fi

}

_gids () 

{ 

    if type getent >&/dev/null; then

        COMPREPLY=($( getent group | 			    awk -F: '{if ($3 ~ /^'$cur'/) print $3}' ));

    else

        if type perl >&/dev/null; then

            COMPREPLY=($( compgen -W '$( perl -e '"'"'while (($gid) = (getgrent)[2]) { print $gid . "\n" }'"'"' )' -- $cur ));

        else

            COMPREPLY=($( awk 'BEGIN {FS=":"} {if ($3 ~ /^'$cur'/) print $3}'			    /etc/group ));

        fi;

    fi

}

_gpg () 

{ 

    local cur prev;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case "$prev" in 

        -@(s|-sign|-clearsign|-decrypt-files|-load-extension))

            _filedir;

            return 0

        ;;

        --@(export|@(?(l|nr|nrl)sign|edit)-key))

            COMPREPLY=($( compgen -W "$( gpg --list-keys 2>/dev/null | sed -ne 's@^pub.*/\([^ ]*\).*\(<\([^>]*\)>\).*$@\1 \3@p')" -- "$cur" ));

            return 0

        ;;

        -@(r|-recipient))

            COMPREPLY=($( compgen -W "$( gpg --list-keys 2>/dev/null | sed -ne 's@^pub.*<\([^>]*\)>.*$@\1@p')" -- "$cur" ));

            if [ -e ~/.gnupg/gpg.conf ]; then

                COMPREPLY=(${COMPREPLY[@]} $( compgen -W "$( sed -ne 's@^[ \t]*group[ \t][ \t]*\([^=]*\).*$@\1@p' ~/.gnupg/gpg.conf  )" -- "$cur"));

            fi;

            return 0

        ;;

    esac;

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( compgen -W '-s -b -e -f -c -d -a -r -u -Z -o -v\

				-q -n -N $(gpg --dump-options)' -- $cur ));

    fi

}

_gzip () 

{ 

    local cur prev xspec IFS='	

';

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( compgen -W '-c -d -f \

			-h -l -L -n -N -q -r -S -t -v -V \

			-1 -2 -3 -4 -5 -6 -7 -8 -9 \

			--stdout --decompress --force --help --list \

			--license --no-name --name --quiet --recursive \

			--suffix --test --verbose --version --fast \

			--best' -- $cur ));

        return 0;

    fi;

    xspec="*.?(t)gz";

    if [[ "$prev" == --* ]]; then

        [[ "$prev" == --decompress || "$prev" == --list || "$prev" == --test ]] && xspec="!"$xspec;

        [[ "$prev" == --force ]] && xspec=;

    else

        if [[ "$prev" == -* ]]; then

            [[ "$prev" == -*[dlt]* ]] && xspec="!"$xspec;

            [[ "$prev" == -*f* ]] && xspec=;

        else

            if [ "$prev" = '>' ]; then

                xspec=;

            fi;

        fi;

    fi;

    _expand || return 0;

    COMPREPLY=($( compgen -f -X "$xspec" -- $cur ) $( compgen -d -- $cur ))

}

_iconv () 

{ 

    local cur prev;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case "$prev" in 

        -@(f|t|-@(from|to)-code))

            COMPREPLY=($( compgen -W 			    '$( iconv --list | sed -e "s@//@@;" )' -- "$cur" ));

            return 0

        ;;

    esac;

    if [[ "$cur" = -* ]]; then

        COMPREPLY=($( compgen -W '--from-code -f --to-code -t --list

		--output -o --verbose' -- "$cur" ));

        return 0;

    fi

}

_id () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( compgen -W '-a -g --group -G --groups -n --name\

			-r --real -u --user --help --version' -- $cur ));

    else

        COMPREPLY=($( compgen -u $cur  ));

    fi

}

_ifupdown () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    if [ $COMP_CWORD -eq 1 ]; then

        _configured_interfaces;

    fi;

    return 0

}

_info () 

{ 

    local cur infopath UNAME;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    _expand || return 0;

    if [[ "$cur" == */* ]]; then

        _filedir;

        return 0;

    fi;

    infopath='/usr/share/info';

    if [ "${INFOPATH: -1:1}" == ':' ]; then

        infopath=${INFOPATH}${infopath};

    else

        if [ ${INFOPATH:+set} ]; then

            infopath=$INFOPATH;

        fi;

    fi;

    infopath=$infopath:;

    if [ -n "$cur" ]; then

        infopath="${infopath//://$cur* }";

    else

        infopath="${infopath//:// }";

    fi;

    COMPREPLY=($( eval command ls "$infopath" 2>/dev/null ));

    COMPREPLY=(${COMPREPLY[@]##*/?(:)});

    for ((i=0 ; i < ${#COMPREPLY[@]} ; ++i ))

    do

        if [ "${COMPREPLY[$i]}" == 'dir' ]; then

            unset COMPREPLY[$i];

        fi;

    done;

    COMPREPLY=(${COMPREPLY[@]%.@(gz|bz2)});

    COMPREPLY=($( compgen -W '${COMPREPLY[@]%.*}' -- "${cur//\\\\/}" ));

    return 0

}

_insmod () 

{ 

    local cur prev modpath;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    if [ $1 = "modprobe" ] && [ "${COMP_WORDS[1]}" = "-r" ]; then

        COMPREPLY=($( /sbin/lsmod | 				awk '{if (NR != 1 && $1 ~ /^'$cur'/) print $1}' ));

        return 0;

    fi;

    if [[ "$cur" == */* ]]; then

        _filedir '@(?(k)o?(.gz))';

        return 0;

    fi;

    if [ $COMP_CWORD -gt 1 ] && [[ "${COMP_WORDS[COMP_CWORD-1]}" != -* ]]; then

        COMPREPLY=($( /sbin/modinfo -p ${COMP_WORDS[1]} 2>/dev/null | 		       awk '{if ($1 ~ /^parm:/ && $2 ~ /^'$cur'/) { print $2 } \

			else if ($1 !~ /:/ && $1 ~ /^'$cur'/) { print $1 }}' ));

    else

        _modules $(uname -r);

    fi;

    return 0

}

_invoke_rc_d () 

{ 

    local cur prev sysvdir services options valid_options;

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    [ -d /etc/rc.d/init.d ] && sysvdir=/etc/rc.d/init.d || sysvdir=/etc/init.d;

    services=($(echo $sysvdir/!(README*|*.sh|*.dpkg*|*.rpm*)));

    services=(${services[@]#$sysvdir/});

    options=(--help --quiet --force --try-anyway --disclose-deny --query --no-fallback);

    if [[ ( $COMP_CWORD -eq 1 ) || ( "$prev" == --* ) ]]; then

        valid_options=($( 	    echo ${COMP_WORDS[@]} ${options[@]} 	    | tr " " "\n" 	    | sed -ne "/$( echo ${options[@]} | sed "s/ /\\\\|/g" )/p" 	    | sort | uniq -u 	    ));

        COMPREPLY=($( compgen -W '${valid_options[@]} ${services[@]}' -- 	    $cur ));

    else

        if [ -x $sysvdir/$prev ]; then

            COMPREPLY=($( compgen -W '`sed -ne "y/|/ /; \

					    s/^.*Usage:[ ]*[^ ]*[ ]*{*\([^}\"]*\).*$/\1/p" \

					    $sysvdir/$prev`' -- 	    $cur ));

        else

            COMPREPLY=();

        fi;

    fi;

    return 0

}

_iptables () 

{ 

    local cur prev table chain;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    chain='s/^Chain \([^ ]\+\).*$/\1/p';

    if [[ $COMP_LINE == *-t\ *filter* ]]; then

        table="-t filter";

    else

        if [[ $COMP_LINE == *-t\ *nat* ]]; then

            table="-t nat";

        else

            if [[ $COMP_LINE == *-t\ *mangle* ]]; then

                table="-t mangle";

            fi;

        fi;

    fi;

    case "$prev" in 

        -*[AIDRPFXLZ])

            COMPREPLY=($( compgen -W '`iptables $table -nL | \

			    sed -ne "s/^Chain \([^ ]\+\).*$/\1/p"`' -- $cur ))

        ;;

        -*t)

            COMPREPLY=($( compgen -W 'nat filter mangle' -- $cur ))

        ;;

        -j)

            if [ "$table" = "-t filter" -o "$table" = "" ]; then

                COMPREPLY=($( compgen -W 'ACCEPT DROP LOG ULOG REJECT \

		    `iptables $table -nL | sed -ne "$chain" \

		    -e "s/INPUT|OUTPUT|FORWARD|PREROUTING|POSTROUTING//"`' -- 		    $cur ));

            else

                if [ "$table" = "-t nat" ]; then

                    COMPREPLY=($( compgen -W 'ACCEPT DROP LOG ULOG REJECT \

		    MIRROR SNAT DNAT MASQUERADE `iptables $table -nL | \

		    sed -ne "$chain" -e "s/OUTPUT|PREROUTING|POSTROUTING//"`' 		    -- $cur ));

                else

                    if [ "$table" = "-t mangle" ]; then

                        COMPREPLY=($( compgen -W 'ACCEPT DROP LOG ULOG REJECT \

		    MARK TOS `iptables $table -nL | sed -ne "$chain" \

		    -e "s/INPUT|OUTPUT|FORWARD|PREROUTING|POSTROUTING//"`' -- 		    $cur ));

                    fi;

                fi;

            fi

        ;;

        *)

            if [[ "$cur" == -* ]]; then

                COMPREPLY=($( compgen -W '-i -o -s -d -p -f -m --append \

		    --delete --insert --replace --list --flush --zero --new \

		    --delete-chain --policy --rename-chain --proto --source \

		    --destination --in-interface --jump --match --numeric \

		    --out-interface --table --verbose --line-numbers --exact \

		    --fragment --modprobe= --set-counters --version' -- "$cur"));

            fi

        ;;

    esac

}

_iwconfig () 

{ 

    local cur prev;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case $prev in 

        mode)

            COMPREPLY=($( compgen -W 'managed ad-hoc master \

				repeater secondary monitor' -- $cur ));

            return 0

        ;;

        essid)

            COMPREPLY=($( compgen -W 'on off any' -- $cur ));

            if [ -n "${COMP_IWLIST_SCAN:-}" ]; then

                COMPREPLY=(${COMPREPLY[@]:-} $( iwlist ${COMP_WORDS[1]} scan | 					awk -F '"' '/ESSID/ {print $2}' | 					grep "^$cur" ));

            fi;

            return 0

        ;;

        nwid)

            COMPREPLY=($( compgen -W 'on off' -- $cur ));

            return 0

        ;;

        channel)

            COMPREPLY=($( iwlist ${COMP_WORDS[1]} channel | 				awk '/^[[:space:]]*Channel/ {print $2}' | 				grep "^$cur" ));

            return 0

        ;;

        freq)

            COMPREPLY=($( iwlist ${COMP_WORDS[1]} channel | 				awk '/^[[:space:]]*Channel/ {print $4"G"}' | 				grep "^$cur" ));

            return 0

        ;;

        ap)

            COMPREPLY=($( compgen -W 'on off any' -- $cur ));

            if [ -n "${COMP_IWLIST_SCAN:-}" ]; then

                COMPREPLY=(${COMPREPLY[@]:-} $( iwlist ${COMP_WORDS[1]} scan | 					awk -F ': ' '/Address/ {print $2}' | 					grep "^$cur" ));

            fi;

            return 0

        ;;

        rate)

            COMPREPLY=($( compgen -W 'auto fixed' -- $cur ));

            COMPREPLY=(${COMPREPLY[@]:-} $( iwlist ${COMP_WORDS[1]} rate | 				awk '/^[[:space:]]*[0-9]/ {print $1"M"}' | 				grep "^$cur" ));

            return 0

        ;;

        rts)

            COMPREPLY=($( compgen -W 'auto fixed off' -- $cur ));

            return 0

        ;;

        frag)

            COMPREPLY=($( compgen -W 'auto fixed off' -- $cur ));

            return 0

        ;;

        key)

            COMPREPLY=($( compgen -W 'off on open restricted' -- $cur ));

            return 0

        ;;

        enc)

            COMPREPLY=($( compgen -W 'off on open restricted' -- $cur ));

            return 0

        ;;

        power)

            COMPREPLY=($( compgen -W 'period timeout off on' -- $cur ));

            return 0

        ;;

        txpower)

            COMPREPLY=($( compgen -W 'off on auto' -- $cur ));

            return 0

        ;;

        retry)

            COMPREPLY=($( compgen -W 'limit lifetime' -- $cur ));

            return 0

        ;;

    esac;

    if [ $COMP_CWORD -eq 1 ]; then

        if [[ "$cur" == -* ]]; then

            COMPREPLY=($( compgen -W '--help --version' -- $cur ));

        else

            _available_interfaces -w;

        fi;

    else

        COMPREPLY=($( compgen -W 'essid nwid mode freq channel sens mode \

			ap nick rate rts frag enc key power txpower commit' -- $cur ));

    fi

}

_iwlist () 

{ 

    local cur prev;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    if [ $COMP_CWORD -eq 1 ]; then

        if [[ "$cur" == -* ]]; then

            COMPREPLY=($( compgen -W '--help --version' -- $cur ));

        else

            _available_interfaces -w;

        fi;

    else

        COMPREPLY=($( compgen -W 'scan scanning freq frequency \

			channel rate bit bitrate key enc encryption power \

			txpower retry ap accesspoint peers event' -- $cur ));

    fi

}

_iwpriv () 

{ 

    local cur prev;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case "$prev" in 

        roam)

            COMPREPLY=($( compgen -W 'on off' -- $cur ));

            return 0

        ;;

        port)

            COMPREPLY=($( compgen -W 'ad-hoc managed' -- $cur ));

            return 0

        ;;

    esac;

    if [ $COMP_CWORD -eq 1 ]; then

        if [[ "$cur" == -* ]]; then

            COMPREPLY=($( compgen -W '--help --version' -- $cur ));

        else

            _available_interfaces -w;

        fi;

    else

        COMPREPLY=($( compgen -W '--all roam port' -- $cur ));

    fi

}

_iwspy () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    if [ $COMP_CWORD -eq 1 ]; then

        if [[ "$cur" == -* ]]; then

            COMPREPLY=($( compgen -W '--help --version' -- $cur ));

        else

            _available_interfaces -w;

        fi;

    else

        COMPREPLY=($( compgen -W 'setthr getthr off' -- $cur ));

    fi

}

_java () 

{ 

    local cur prev i;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    for ((i=1; i < $COMP_CWORD; i++))

    do

        case ${COMP_WORDS[$i]} in 

            -cp | -classpath)

                ((i++))

            ;;

            -*)



            ;;

            *)

                _filedir;

                return 0

            ;;

        esac;

    done;

    case $prev in 

        -@(cp|classpath))

            _java_path;

            return 0

        ;;

    esac;

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( compgen -W '-client -hotspot -server -classic \

				-cp -classpath -D -verbose -verbose:class \

				-verbose:gc -version:jni -version \

				-showversion -? -help -X -jar \

				-ea -enableassertions -da -disableassertions \

				-esa -enablesystemassertions \

				-dsa -disablesystemassertions ' -- $cur ));

    else

        if [[ "$prev" == -jar ]]; then

            _filedir jar;

        else

            _java_classes;

        fi;

    fi

}

_java_classes () 

{ 

    local classpath i;

    _java_find_classpath;

    cur=${cur//.//};

    for i in ${classpath//:/ };

    do

        if [ -r $i ] && [[ "$i" == *.@(jar|zip) ]]; then

            if type zipinfo >&/dev/null; then

                COMPREPLY=(${COMPREPLY[@]} $( zipinfo -1 				"$i" | grep "^$cur" | grep '\.class$' | 				grep -v "\\$" ));

            else

                COMPREPLY=(${COMPREPLY[@]} $( jar tf "$i" 				"$cur" | grep "\.class$" | grep -v "\\$" ));

            fi;

        else

            if [ -d $i ]; then

                i=${i%/};

                COMPREPLY=(${COMPREPLY[@]} $( find "$i" -type f 			-path "$i/$cur*.class" 2>/dev/null | 			grep -v "\\$" | sed -e "s|^$i/||" ));

            fi;

        fi;

    done;

    COMPREPLY=(${COMPREPLY[@]%.class});

    COMPREPLY=(${COMPREPLY[@]//\//.})

}

_java_find_classpath () 

{ 

    local i;

    for ((i=1; i < COMP_CWORD; i++ ))

    do

        if [[ "${COMP_WORDS[i]}" == -@(cp|classpath) ]]; then

            classpath=${COMP_WORDS[i+1]};

            break;

        fi;

    done;

    [ -z "$classpath" ] && classpath=$CLASSPATH;

    [ -z "$classpath" ] && classpath=.

}

_java_find_sourcepath () 

{ 

    local i;

    for ((i=1; i < COMP_CWORD; i++ ))

    do

        if [[ "${COMP_WORDS[i]}" == -sourcepath ]]; then

            sourcepath=${COMP_WORDS[i+1]};

            break;

        fi;

    done;

    [ -z "$sourcepath" ] && _java_find_classpath;

    sourcepath=$classpath

}

_java_packages () 

{ 

    local sourcepath i;

    _java_find_sourcepath;

    cur=${cur//.//};

    for i in ${sourcepath//:/ };

    do

        if [ -d $i ]; then

            COMPREPLY=(${COMPREPLY[@]} $( command ls -F -d 				$i/$cur* 2>/dev/null | sed -e 's|^'$i'/||' ));

        fi;

    done;

    COMPREPLY=($( echo ${COMPREPLY[@]} | tr " " "\n" | grep "/$" ));

    COMPREPLY=(${COMPREPLY[@]%/});

    cur=${COMPREPLY[@]//\//.}

}

_java_path () 

{ 

    cur=${cur##*:};

    _filedir '@(jar|zip)'

}

_kill () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    if [ $COMP_CWORD -eq 1 ] && [[ "$cur" == -* ]]; then

        _signals;

    else

        _pids;

    fi

}

_killall () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    if [ $COMP_CWORD -eq 1 ] && [[ "$cur" == -* ]]; then

        _signals;

    else

        COMPREPLY=($( compgen -W '$( command ps axo command | \

			      sed -ne "1d; s/^\[\?\([^-][^] ]*\).*$/\1/p" | \

			      sed -e "s/.*\///" )' -- $cur ));

    fi;

    return 0

}

_known_hosts () 

{ 

    local cur curd ocur user suffix aliases global_kh user_kh hosts i host;

    local -a kh khd config;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    ocur=$cur;

    [ "$1" = -a ] || [ "$2" = -a ] && aliases='yes';

    [ "$1" = -c ] || [ "$2" = -c ] && suffix=':';

    [[ $cur == *@* ]] && user=${cur%@*}@ && cur=${cur#*@};

    kh=();

    [ -r /etc/ssh/ssh_config ] && config=(${config[@]} /etc/ssh/ssh_config);

    [ -r ~/.ssh/config ] && config=(${config[@]} ~/.ssh/config);

    [ -r ~/.ssh2/config ] && config=(${config[@]} ~/.ssh2/config);

    if [ ${#config[@]} -gt 0 ]; then

        global_kh=$( eval echo $( sed -ne 's/^[Gg][Ll][Oo][Bb][Aa][Ll][Kk][Nn][Oo][Ww][Nn][Hh][Oo][Ss][Tt][Ss][Ff][Ii][Ll][Ee]['"$'\t '"']*\(.*\)$/\1/p' ${config[@]} ) );

        user_kh=$( eval echo $( sed -ne 's/^[Uu][Ss][Ee][Rr][Kk][Nn][Oo][Ww][Nn][Hh][Oo][Ss][Tt][Ss][Ff][Ii][Ll][Ee]['"$'\t '"']*\(.*\)$/\1/p' ${config[@]} ) );

    fi;

    if [ -r "$global_kh" ]; then

        kh=("$global_kh");

    else

        [ -r /etc/ssh/ssh_known_hosts ] && kh=(${kh[@]} /etc/ssh/ssh_known_hosts);

        [ -r /etc/ssh/ssh_known_hosts2 ] && kh=(${kh[@]} /etc/ssh/ssh_known_hosts2);

        [ -r /etc/known_hosts ] && kh=(${kh[@]} /etc/known_hosts);

        [ -r /etc/known_hosts2 ] && kh=(${kh[@]} /etc/known_hosts2);

        [ -d /etc/ssh2/knownhosts ] && khd=(${khd[@]} /etc/ssh2/knownhosts/*pub);

    fi;

    if [ -r "$user_kh" ]; then

        kh=(${kh[@]} "$user_kh");

    else

        [ -r ~/.ssh/known_hosts ] && kh=(${kh[@]} ~/.ssh/known_hosts);

        [ -r ~/.ssh/known_hosts2 ] && kh=(${kh[@]} ~/.ssh/known_hosts2);

        [ -d ~/.ssh2/hostkeys ] && khd=(${khd[@]} ~/.ssh2/hostkeys/*pub);

    fi;

    if [ ${#kh[@]} -gt 0 -o ${#khd[@]} -gt 0 ]; then

        cur=${cur//\//\\\/};

        cur=${cur//\./\\\.};

        curd=$cur;

        if [[ "$cur" == [0-9]*.* ]]; then

            cur="^$cur.*";

        else

            if [[ "$cur" == [0-9]* ]]; then

                cur="^$cur.*\.";

            else

                if [ -z "$cur" ]; then

                    cur="[a-z.]";

                else

                    cur="^$cur";

                fi;

            fi;

        fi;

        if [ ${#kh[@]} -gt 0 ]; then

            COMPREPLY=($( awk 'BEGIN {FS=","}

				{for (i=1; i<=2; ++i) { \

				       gsub(" .*$", "", $i); \

				       if ($i ~ /'$cur'/) {print $i} \

				}}' ${kh[@]} 2>/dev/null ));

        fi;

        if [ ${#khd[@]} -gt 0 ]; then

            for i in ${khd[@]};

            do

                if [[ "$i" == *key_22_$curd*.pub ]] && [ -r "$i" ]; then

                    host=${i/#*key_22_/};

                    host=${host/%.pub/};

                    COMPREPLY=(${COMPREPLY[@]} $host);

                fi;

            done;

        fi;

        if [ ${#config[@]} -gt 0 ] && [ -n "$aliases" ]; then

            hosts=$( compgen -W "$( sed -ne 's/^[Hh][Oo][Ss][Tt]['"$'\t '"']*\([^*?]*\)$/\1/p' ${config[@]} )" -- $ocur );

            COMPREPLY=(${COMPREPLY[@]} $hosts);

        fi;

        for ((i=0; i < ${#COMPREPLY[@]}; i++ ))

        do

            COMPREPLY[i]=$user${COMPREPLY[i]}$suffix;

        done;

    else

        COMPREPLY=($( compgen -A hostname -S "$suffix" -- $cur ));

    fi;

    return 0

}

_lftp () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    if [ $COMP_CWORD -eq 1 ] && [ -f ~/.lftp/bookmarks ]; then

        COMPREPLY=($( compgen -W '$( sed -ne "s/^\(.*\)''	''.*$/\1/p" \

			   ~/.lftp/bookmarks )' -- $cur ));

    fi;

    return 0

}

_longopt () 

{ 

    local cur opt;

    cur=${COMP_WORDS[COMP_CWORD]};

    if [[ "$cur" == --*=* ]]; then

        opt=${cur%%=*};

        opt=${opt%\\*};

        cur=${cur#*=};

        _filedir;

        COMPREPLY=($( compgen -P "$opt=" -W '${COMPREPLY[@]}' -- $cur));

        return 0;

    fi;

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( $1 --help 2>&1 | sed -e '/--/!d' 				-e 's/.*\(--[-A-Za-z0-9]\+=\?\).*/\1/' | 			       command grep "^$cur" | sort -u ));

    else

        if [[ "$1" == @(mk|rm)dir ]]; then

            _filedir -d;

        else

            _filedir;

        fi;

    fi

}

_look () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    if [ $COMP_CWORD = 1 ]; then

        COMPREPLY=($( compgen -W '$(look $cur)' ));

    fi

}

_make () 

{ 

    local file makef makef_dir="." makef_inc cur prev i;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case $prev in 

        -@(f|o|W))

            _filedir;

            return 0

        ;;

        -@(I|C))

            _filedir -d;

            return 0

        ;;

    esac;

    if [[ "$cur" == *=* ]]; then

        prev=${cur/=*/};

        cur=${cur/*=/};

        case "$prev" in 

            --@(file|makefile))

                _filedir;

                return 0

            ;;

            --@(directory|include-dir))

                _filedir -d;

                return 0

            ;;

        esac;

    fi;

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( compgen -W '-b -m -B -C -d -e -f -h -i -I\

			-j -l -k -n -o -p -q -r -R - s -S -t -v -w -W \

			--always-make --directory= --debug \

			--environment-overrides --file= --makefile= --help \

			--ignore-errors --include-dir= --jobs --load-average \

			--max-load --keep-going --just-print --dry-run \

			--recon --old-file= --assume-old= --print-data-base \

			--question --no-builtin-rules --no-builtin-variables \

			--silent --quiet --no-keep-goind --stop --touch \

			--version --print-directory --no-print-directory \

			--what-if= --new-file= --assume-new= \

			--warn-undefined-variables' -- $cur ));

    else

        for ((i=0; i < ${#COMP_WORDS[@]}; i++ ))

        do

            if [[ ${COMP_WORDS[i]} == -C ]]; then

                eval makef_dir=${COMP_WORDS[i+1]};

                break;

            fi;

        done;

        if [ -f ${makef_dir}/GNUmakefile ]; then

            makef=${makef_dir}/GNUmakefile;

        else

            if [ -f ${makef_dir}/makefile ]; then

                makef=${makef_dir}/makefile;

            else

                if [ -f ${makef_dir}/Makefile ]; then

                    makef=${makef_dir}/Makefile;

                else

                    makef=${makef_dir}/*.mk;

                fi;

            fi;

        fi;

        for ((i=0; i < ${#COMP_WORDS[@]}; i++ ))

        do

            if [[ ${COMP_WORDS[i]} == -f ]]; then

                eval makef=${COMP_WORDS[i+1]};

                break;

            fi;

        done;

        [ ! -f $makef ] && return 0;

        makef_inc=$( grep -E '^-?include' $makef | sed -e "s,^.* ,"$makef_dir"/," );

        for file in $makef_inc;

        do

            [ -f $file ] && makef="$makef $file";

        done;

        COMPREPLY=($( awk -F':' '/^[a-zA-Z0-9][^$#\/\t=]*:([^=]|$)/ \

				{split($1,A,/ /);for(i in A)print A[i]}' 				$makef 2>/dev/null | command grep "^$cur" ));

    fi

}

_man () 

{ 

    local cur prev sect manpath UNAME;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    _expand || return 0;

    if [[ "$cur" == */* ]]; then

        _filedir;

        return 0;

    fi;

    UNAME=$( uname -s );

    UNAME=${UNAME/CYGWIN_*/Cygwin};

    if [ $UNAME = GNU -o $UNAME = Linux -o $UNAME = FreeBSD -o $UNAME = Cygwin ]; then

        manpath=$( manpath 2>/dev/null || command man --path );

    else

        manpath=$MANPATH;

    fi;

    if [ -z "$manpath" ]; then

        COMPREPLY=($( compgen -c -- $cur ));

        return 0;

    fi;

    [[ "$prev" == [0-9ln] ]] && sect=$prev || sect='*';

    manpath=$manpath:;

    if [ -n "$cur" ]; then

        manpath="${manpath//://*man$sect/$cur* } ${manpath//://*cat$sect/$cur* }";

    else

        manpath="${manpath//://*man$sect/ } ${manpath//://*cat$sect/ }";

    fi;

    COMPREPLY=($( eval command ls "$manpath" 2>/dev/null ));

    COMPREPLY=(${COMPREPLY[@]##*/?(:)});

    COMPREPLY=(${COMPREPLY[@]%.@(gz|bz2)});

    COMPREPLY=($( compgen -W '${COMPREPLY[@]%.*}' -- "${cur//\\\\/}" ));

    [[ "$prev" != [0-9ln] ]] && _filedir '[0-9ln]';

    return 0

}

_modules () 

{ 

    local modpath;

    modpath=/lib/modules/$1;

    COMPREPLY=($( command ls -R $modpath | 			sed -ne 's/^\('$cur'.*\)\.k\?o\(\|.gz\)$/\1/p'))

}

_mount () 

{ 

    local cur i sm host;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    [[ "$cur" == \\ ]] && cur="/";

    for i in {,/usr}/{,s}bin/showmount;

    do

        [ -x $i ] && sm=$i && break;

    done;

    if [ -n "$sm" ] && [[ "$cur" == *:* ]]; then

        COMPREPLY=($( $sm -e ${cur%%:*} | sed 1d | 			       grep ^${cur#*:} | awk '{print $1}' ));

    else

        if [[ "$cur" == //* ]]; then

            host=${cur#//};

            host=${host%%/*};

            if [ -n "$host" ]; then

                COMPREPLY=($( compgen -W "$( echo $( smbclient -d 0 -NL $host 2>/dev/null|

			sed -ne '/^['"$'\t '"']*Sharename/,/^$/p' |

			sed -ne '3,$s|^[^A-Za-z]*\([^'"$'\t '"']*\).*$|//'$host'/\1|p' ) )" -- "$cur" ));

            fi;

        else

            if [ -r /etc/vfstab ]; then

                COMPREPLY=($( awk '! /^[ \t]*#/ {if ($3 ~ /\//) print $3}' 				/etc/vfstab | grep "^$cur" ));

            else

                if [ ! -e /etc/fstab ]; then

                    COMPREPLY=($( mount | awk '! /^[ \t]*#/ {if ($3 ~ /\//) print $3}' 				 | grep "^$cur" ));

                else

                    COMPREPLY=($( awk '! /^[ \t]*#/ {if ($2 ~ /\//) print $2}' 				/etc/fstab | grep "^$cur" ));

                fi;

            fi;

        fi;

    fi;

    return 0

}

_nslookup () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]#-};

    COMPREPLY=($( compgen -P '-' -W 'all class= debug d2 domain= \

			       srchlist= defname search port= querytype= \

			       type= recurse retry root timeout vc \

			       ignoretc' -- $cur ))

}

_ntpdate () 

{ 

    local cur prev;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case $prev in 

        -k)

            _filedir;

            return 0

        ;;

        -U)

            COMPREPLY=($( compgen -u $cur  ));

            return 0

        ;;

    esac;

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( compgen -W '-4 -6 -b -B -d -Q -q -s -u -v -a\

			-e -k -p -o -r -t' -- $cur ));

    else

        _known_hosts;

    fi

}

_ooexp_ () 

{ 

    local c=${COMP_WORDS[COMP_CWORD]};

    local a="${COMP_LINE}";

    local e s g=0 cd dc t="";

    local IFS;

    shopt -q extglob && g=1;

    test $g -eq 0 && shopt -s extglob;

    cd='*-?(c)d*';

    dc='*-d?(c)*';

    case "${1##*/}" in 

        oobase)

            e='!*.+(odb|ODB)'

        ;;

        oofromtemplate)

            e='!*.+(stw|STW|dot|DOT|vor|VOR|stc|STC|xlt|XLT|sti|STI|pot|POT|std|STD|stw|STW|dotm|DOTM|dotx|DOTX|potm|POTM|potx|POTX|xltm|XLTM|xltx|XLTX)'

        ;;

        oodraw)

            e='!*.+(sxd|SXD|std|STD|dxf|DXF|emf|EMF|eps|EPS|met|MET|pct|PCT|sgf|SGF|sgv|SGV|sda|SDA|sdd|SDD|vor|VOR|svm|SVM|wmf|WMF|bmp|BMP|gif|GIF|jpg|JPG|jpeg|JPEG|jfif|JFIF|fif|FIF|jpe|JPE|pcd|PCD|pcx|PCX|pgm|PGM|png|PNG|ppm|PPM|psd|PSD|ras|RAS|tga|TGA|tif|TIF|tiff|TIFF|xbm|XBM|xpm|XPM|odg|ODG|otg|OTG|odc|ODC|odi|ODI|sds|SDS|wpg|WPG)'

        ;;

        oocalc)

            e='!*.+(sxc|SXC|stc|STC|dif|DIF|dbf|DBF|xls|XLS|xlw|XLW|xlt|XLT|rtf|RTF|sdc|SDC|vor|VOR|slk|SLK|txt|TXT|htm|HTM|html|HTML|wk1|WK1|wks|WKS|123|123|xml|XML|ods|ODS|ots|OTS|csv|CSV|xlsb|XLSB|xlsm|XLSM|xlsx|XLSX|xltm|XLTM|xltx|XLTX)'

        ;;

        oomath)

            e='!*.+(sxm|SXM|smf|SMF|mml|MML|odf|ODF)'

        ;;

        ooweb)

            e='!*.+(htm|HTM|html|HTML|stw|STW|txt|TXT|vor|VOR|oth|OTH)'

        ;;

        ooffice)

            e='!*.+(sxd|SXD|std|STD|dxf|DXF|emf|EMF|eps|EPS|met|MET|pct|PCT|sgf|SGF|sgv|SGV|sda|SDA|sdd|SDD|vor|VOR|svm|SVM|wmf|WMF|bmp|BMP|gif|GIF|jpg|JPG|jpeg|JPEG|jfif|JFIF|fif|FIF|jpe|JPE|pcd|PCD|pcx|PCX|pgm|PGM|png|PNG|ppm|PPM|psd|PSD|ras|RAS|tga|TGA|tif|TIF|tiff|TIFF|xbm|XBM|xpm|XPM|odg|ODG|otg|OTG|odc|ODC|odi|ODI|sds|SDS|wpg|WPG|doc|DOC|dot|DOT|rtf|RTF|sxw|SXW|stw|STW|sdw|SDW|vor|VOR|txt|TXT|htm?|HTM?|xml|XML|wp|WP|wpd|WPD|odt|ODT|ott|OTT|docm|DOCM|docx|DOCX|dotm|DOTM|dotx|DOTX|sxm|SXM|smf|SMF|mml|MML|odf|ODF|sxi|SXI|sti|STI|ppt|PPT|pps|PPS|pot|POT|sxd|SXD|sda|SDA|sdd|SDD|sdp|SDP|vor|VOR|cgm|CGM|odp|ODP|otp|OTP|ppsm|PPSM|ppsx|PPSX|pptm|PPTM|pptx|PPTX|potm|POTM|potx|POTX|odb|ODB|sxc|SXC|stc|STC|dif|DIF|dbf|DBF|xls|XLS|xlw|XLW|xlt|XLT|rtf|RTF|sdc|SDC|vor|VOR|slk|SLK|txt|TXT|htm|HTM|html|HTML|wk1|WK1|wks|WKS|123|123|xml|XML|ods|ODS|ots|OTS|csv|CSV|xlsb|XLSB|xlsm|XLSM|xlsx|XLSX|xltm|XLTM|xltx|XLTX|sxg|SXG|xgl|XGL|txt|TXT|odm|ODM|sgl|SGL|stw|STW|dot|DOT|vor|VOR|stc|STC|xlt|XLT|sti|STI|pot|POT|std|STD|stw|STW|dotm|DOTM|dotx|DOTX|potm|POTM|potx|POTX|xltm|XLTM|xltx|XLTX|htm|HTM|html|HTML|stw|STW|txt|TXT|vor|VOR|oth|OTH)'

        ;;

        oowriter)

            e='!*.+(doc|DOC|dot|DOT|rtf|RTF|sxw|SXW|stw|STW|sdw|SDW|vor|VOR|txt|TXT|htm?|HTM?|xml|XML|wp|WP|wpd|WPD|odt|ODT|ott|OTT|docm|DOCM|docx|DOCX|dotm|DOTM|dotx|DOTX)'

        ;;

        ooimpress)

            e='!*.+(sxi|SXI|sti|STI|ppt|PPT|pps|PPS|pot|POT|sxd|SXD|sda|SDA|sdd|SDD|sdp|SDP|vor|VOR|cgm|CGM|odp|ODP|otp|OTP|ppsm|PPSM|ppsx|PPSX|pptm|PPTM|pptx|PPTX|potm|POTM|potx|POTX)'

        ;;

        *)

            e='!*'

        ;;

    esac;

    case "$(complete -p ${1##*/} 2> /dev/null)" in 

        *-d*)



        ;;

        *)

            s="-S/"

        ;;

    esac;

    IFS='

';

    case "$c" in 

        \$\(*\))

            eval COMPREPLY=\(${c}\)

        ;;

        \$\(*)

            COMPREPLY=($(compgen -c -P '$(' -S ')'  -- ${c#??}))

        ;;

        \`*\`)

            eval COMPREPLY=\(${c}\)

        ;;

        \`*)

            COMPREPLY=($(compgen -c -P '\`' -S '\`' -- ${c#?}))

        ;;

        \$\{*\})

            eval COMPREPLY=\(${c}\)

        ;;

        \$\{*)

            COMPREPLY=($(compgen -v -P '${' -S '}'  -- ${c#??}))

        ;;

        \$*)

            COMPREPLY=($(compgen -v -P '$'          -- ${c#?}))

        ;;

        \~*/*)

            COMPREPLY=($(compgen -f -X "$e"         -- ${c}))

        ;;

        \~*)

            COMPREPLY=($(compgen -u ${s}	 	-- ${c}))

        ;;

        *@*)

            COMPREPLY=($(compgen -A hostname -P '@' -S ':' -- ${c#*@}))

        ;;

        *[*?[]*)

            COMPREPLY=($(compgen -G "${c}"))

        ;;

        *[?*+\!@]\(*\)*)

            if test $g -eq 0; then

                COMPREPLY=($(compgen -f -X "$e" -- $c));

                test $g -eq 0 && shopt -u extglob;

                return;

            fi;

            COMPREPLY=($(compgen -G "${c}"))

        ;;

        *)

            if test "$c" = ".."; then

                COMPREPLY=($(compgen -d -X "$e" -S / ${_nosp} -- $c));

            else

                for s in $(compgen -f -X "$e" -- $c);

                do

                    if test -d $s; then

                        COMPREPLY=(${COMPREPLY[@]} $(compgen -f -X "$e" -S / -- $s));

                    else

                        if test -z "$t"; then

                            COMPREPLY=(${COMPREPLY[@]} $s);

                        else

                            case "$(file -b $s 2> /dev/null)" in 

                                $t)

                                    COMPREPLY=(${COMPREPLY[@]} $s)

                                ;;

                            esac;

                        fi;

                    fi;

                done;

            fi

        ;;

    esac;

    test $g -eq 0 && shopt -u extglob

}

_openssl () 

{ 

    local cur prev;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    if [ $COMP_CWORD -eq 1 ]; then

        COMPREPLY=($( compgen -W 'asn1parse ca ciphers crl crl2pkcs7 \

			dgst dh dhparam dsa dsaparam enc errstr gendh gendsa \

			genrsa nseq passwd pkcs12 pkcs7 pkcs8 rand req rsa \

			rsautl s_client s_server s_time sess_id smime speed \

			spkac verify version x509 md2 md4 md5 mdc2 rmd160 sha \

			sha1 base64 bf bf-cbc bf-cfb bf-ecb bf-ofb cast \

			cast-cbc cast5-cbc cast5-cfb cast5-ecb cast5-ofb des \

			des-cbc des-cfb des-ecb des-ede des-ede-cbc \

			des-ede-cfb des-ede-ofb des-ede3 des-ede3-cbc \

			des-ede3-cfb des-ede3-ofb des-ofb des3 desx rc2 \

			rc2-40-cbc rc2-64-cbc rc2-cbc rc2-cfb rc2-ecb rc2-ofb \

			rc4 rc4-40' -- $cur ));

    else

        prev=${COMP_WORDS[COMP_CWORD-1]};

        case ${COMP_WORDS[1]} in 

            asn1parse)

                case $prev in 

                    -inform)

                        COMPREPLY=($( compgen -W 'DER PEM' -- $cur ));

                        return 0

                    ;;

                    -@(in|out|oid))

                        _filedir;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-inform -in -out -noout -offset \

						-length -i -oid -strparse' -- $cur ));

                fi

            ;;

            ca)

                case $prev in 

                    -@(config|revoke|cert|in|out|spkac|ss_cert))

                        _filedir;

                        return 0

                    ;;

                    -outdir)

                        _filedir -d;

                        return 0

                    ;;

                    -@(name|crlexts|extensions))

                        _openssl_sections;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-verbose -config -name \

						-gencrl -revoke -crldays -crlhours -crlexts \

						-startdate -enddate -days -md -policy -keyfile \

						-key -passin -cert -in -out -notext -outdir \

						-infiles -spkac -ss_cert -preserveDN -batch \

						-msie_hack -extensions' -- $cur ));

                fi

            ;;

            ciphers)

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-v -ssl2 -ssl3 -tls1' -- $cur ));

                fi

            ;;

            crl)

                case $prev in 

                    -@(in|out)form)

                        COMPREPLY=($( compgen -W 'DER PEM' -- $cur ));

                        return 0

                    ;;

                    -@(in|out|CAfile))

                        _filedir;

                        return 0

                    ;;

                    -CAPath)

                        _filedir -d;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-inform -outform -text -in -out -noout \

						-hash -issuer -lastupdate -nextupdate -CAfile -CApath' -- $cur ));

                fi

            ;;

            crl2pkcs7)

                case $prev in 

                    -@(in|out)form)

                        COMPREPLY=($( compgen -W 'DER PEM' -- $cur ));

                        return 0

                    ;;

                    -@(in|out))

                        _filedir;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-inform -outform -in -out -print_certs' -- $cur ));

                fi

            ;;

            dgst)

                case $prev in 

                    -@(out|sign|verify|prvrify|signature))

                        _filedir;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-md5 -md4 -md2 -sha1 -sha -mdc2 -ripemd160 -dss1 \

						-c -d -hex -binary -out -sign -verify -prverify -signature' -- $cur ));

                else

                    _filedir;

                fi

            ;;

            dsa)

                case $prev in 

                    -@(in|out)form)

                        COMPREPLY=($( compgen -W 'DER PEM' -- $cur ));

                        return 0

                    ;;

                    -@(in|out))

                        _filedir;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-inform -outform -in -passin -out -passout -des -des3 -idea -text -noout \

						-modulus -pubin -pubout' -- $cur ));

                fi

            ;;

            dsaparam)

                case $prev in 

                    -@(in|out)form)

                        COMPREPLY=($( compgen -W 'DER PEM' -- $cur ));

                        return 0

                    ;;

                    -@(in|out|rand))

                        _filedir;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-inform -outform -in -out -noout \

						-text -C -rand -genkey' -- $cur ));

                fi

            ;;

            enc)

                case $prev in 

                    -@(in|out|kfile))

                        _filedir;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-ciphername -in -out -pass \

						-e -d -a -A -k -kfile -S -K -iv -p -P -bufsize -debug' -- $cur ));

                fi

            ;;

            dhparam)

                case $prev in 

                    -@(in|out)form)

                        COMPREPLY=($( compgen -W 'DER PEM' -- $cur ));

                        return 0

                    ;;

                    -@(in|out|rand))

                        _filedir;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-inform -outform -in -out -dsaparam -noout \

						-text -C -2 -5 -rand' -- $cur ));

                fi

            ;;

            gendsa)

                case $prev in 

                    -@(out|rand))

                        _filedir;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-out -des -des3 -idea -rand' -- $cur ));

                else

                    _filedir;

                fi

            ;;

            genrsa)

                case $prev in 

                    -@(out|rand))

                        _filedir;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-out -passout -des -des3 -idea -f4 -3 -rand' -- $cur ));

                fi

            ;;

            pkcs7)

                case $prev in 

                    -@(in|out)form)

                        COMPREPLY=($( compgen -W 'DER PEM' -- $cur ));

                        return 0

                    ;;

                    -@(in|out))

                        _filedir;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-inform -outform -in -out -print_certs -text -noout' -- $cur ));

                fi

            ;;

            rand)

                case $prev in 

                    -@(out|rand))

                        _filedir;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-out -rand -base64' -- $cur ));

                fi

            ;;

            req)

                case "$prev" in 

                    -@(in|out|key)form)

                        COMPREPLY=($( compgen -W 'DER PEM' -- $cur ));

                        return 0

                    ;;

                    -@(in|out|rand|key|keyout|config))

                        _filedir;

                        return 0

                    ;;

                    -extensions)

                        _openssl_sections;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-inform -outform -in \

						-passin -out -passout -text -noout -verify \

						-modulus -new -rand -newkey -newkey -nodes \

						-key -keyform -keyout -md5 -sha1 -md2 -mdc2 \

						-config -x509 -days -asn1-kludge -newhdr \

						-extensions -reqexts section' -- $cur ));

                fi

            ;;

            rsa)

                case $prev in 

                    -@(in|out)form)

                        COMPREPLY=($( compgen -W 'DER NET PEM' -- $cur ));

                        return 0

                    ;;

                    -@(in|out))

                        _filedir;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-inform -outform -in -passin -out -passout \

						-sgckey -des -des3 -idea -text -noout -modulus -check -pubin \

						-pubout -engine' -- $cur ));

                fi

            ;;

            rsautl)

                case $prev in 

                    -@(in|out|inkey))

                        _filedir;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-in -out -inkey -pubin -certin -sign -verify \

						-encrypt -decrypt -pkcs -ssl -raw -hexdump -asn1parse' -- $cur ));

                fi

            ;;

            s_client)

                case $prev in 

                    -connect)

                        _known_hosts;

                        return 0

                    ;;

                    -@(cert|key|CAfile|rand))

                        _filedir;

                        return 0

                    ;;

                    -CApath)

                        _filedir -d;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-connect -verify -cert -key -CApath -CAfile \

						-reconnect -pause -showcerts -debug -msg -nbio_test -state -nbio \

						-crlf -ign_eof -quiet -ssl2 -ssl3 -tls1 -no_ssl2 -no_ssl3 -no_tls1 \

						-bugs -cipher -starttls -engine -rand' -- $cur ));

                fi

            ;;

            s_server)

                case $prev in 

                    -@(cert|key|dcert|dkey|dhparam|CAfile|rand))

                        _filedir;

                        return 0

                    ;;

                    -CApath)

                        _filedir -d;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-accept -context -verify -Verify -cert -key \

						 -dcert -dkey -dhparam -nbio -nbio_test -crlf -debug -msg -state -CApath \

						 -CAfile -nocert -cipher -quiet -no_tmp_rsa -ssl2 -ssl3 -tls1 -no_ssl2 \

						 -no_ssl3 -no_tls1 -no_dhe -bugs -hack -www -WWW -HTTP -engine -id_prefix \

						 -rand' -- $cur ));

                fi

            ;;

            s_time)

                case $prev in 

                    -connect)

                        _known_hosts;

                        return 0

                    ;;

                    -@(cert|key|CAfile))

                        _filedir;

                        return 0

                    ;;

                    -CApath)

                        _filedir -d;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-connect -www -cert -key -CApath -CAfile -reuse \

						-new -verify -nbio -time -ssl2 -ssl3 -bugs -cipher' -- $cur ));

                fi

            ;;

            sess_id)

                case $prev in 

                    -@(in|out)form)

                        COMPREPLY=($( compgen -W 'DER PEM' -- $cur ));

                        return 0

                    ;;

                    -@(in|out))

                        _filedir;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-inform -outform -in -out -text -noout \

						-context ID' -- $cur ));

                fi

            ;;

            smime)

                case $prev in 

                    -@(in|out)form)

                        COMPREPLY=($( compgen -W 'SMIME DER PEM' -- $cur ));

                        return 0

                    ;;

                    -@(in|out|certfile|signer|recip|inkey|content|rand))

                        _filedir;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-encrypt -decrypt -sign -verify -pk7out -des -des3 \

						-rc2-40 -rc2-64 -rc2-128 -aes128 -aes192 -aes256 -in -certfile -signer \

						-recip -inform -passin -inkey -out -outform -content -to -from -subject \

						-text -rand' -- $cur ));

                else

                    _filedir;

                fi

            ;;

            speed)

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-engine' -- $cur ));

                else

                    COMPREPLY=($( compgen -W 'md2 mdc2 md5 hmac sha1 rmd160 idea-cbc \

						rc2-cbc rc5-cbc bf-cbc des-cbc des-ede3 rc4 rsa512 rsa1024 rsa2048 \

						rsa4096 dsa512 dsa1024 dsa2048 idea rc2 des rsa blowfish' -- $cur ));

                fi

            ;;

            verify)

                case $prev in 

                    -@(CAfile|untrusted))

                        _filedir;

                        return 0

                    ;;

                    -CApath)

                        _filedir -d;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-CApath -CAfile -purpose -untrusted -help -issuer_checks \

						-verbose -certificates' -- $cur ));

                else

                    _filedir;

                fi

            ;;

            x509)

                case "$prev" in 

                    -@(in|out|CA|CAkey|CAserial|extfile))

                        _filedir;

                        return 0

                    ;;

                    -@(in|out)form)

                        COMPREPLY=($( compgen -W 'DER PEM NET' -- $cur ));

                        return 0

                    ;;

                    -@(key|CA|CAkey)form)

                        COMPREPLY=($( compgen -W 'DER PEM' -- $cur ));

                        return 0

                    ;;

                    -extensions)

                        _openssl_sections;

                        return 0

                    ;;

                esac;

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-inform -outform \

						-keyform -CAform -CAkeyform -in -out \

						-serial -hash -subject -issuer -nameopt \

						-email -startdate -enddate -purpose \

						-dates -modulus -fingerprint -alias \

						-noout -trustout -clrtrust -clrreject \

						-addtrust -addreject -setalias -days \

						-set_serial -signkey -x509toreq -req \

						-CA -CAkey -CAcreateserial -CAserial \

						-text -C -md2 -md5 -sha1 -mdc2 -clrext \

						-extfile -extensions -engine' -- $cur ));

                fi

            ;;

            @(md5|md4|md2|sha1|sha|mdc2|ripemd160))

                if [[ "$cur" == -* ]]; then

                    COMPREPLY=($( compgen -W '-c -d' -- $cur ));

                else

                    _filedir;

                fi

            ;;

        esac;

    fi;

    return 0

}

_openssl_sections () 

{ 

    local config;

    config=/etc/ssl/openssl.cnf;

    [ ! -f $config ] && config=/usr/share/ssl/openssl.cnf;

    for ((i=2; i < COMP_CWORD; i++ ))

    do

        if [[ "${COMP_WORDS[i]}" == -config ]]; then

            config=${COMP_WORDS[i+1]};

            break;

        fi;

    done;

    [ ! -f $config ] && return 0;

    COMPREPLY=($( awk '/\[.*\]/ {print $2} ' $config | grep "^$cur" ))

}

_perl () 

{ 

    local cur prev prefix temp;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    prefix="";

    if [[ "$cur" == -?* ]]; then

        temp=$cur;

        prev=${temp:0:2};

        cur=${temp:2};

        prefix=$prev;

    fi;

    case "$prev" in 

        -m | -M)

            _perlmodules;

            return 0

        ;;

    esac;

    if [ $COMP_CWORD -eq 1 ] && [[ "$cur" != -* ]]; then

        _filedir;

        return 0;

    fi;

    COMPREPLY=($( compgen -W '-C -s -T -u -U -W -X -h -v -V -c -w -d -D -p \

			-n -a -F -l -0 -I -m -M -P -S -x -i -e ' -- $cur ));

    return 0

}

_perldoc () 

{ 

    local cur prev prefix temp;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    prefix="";

    if [[ "$cur" == -?* ]]; then

        temp=$cur;

        prev=${temp:0:2};

        cur=${temp:2};

        prefix=$prev;

    fi;

    case $prev in 

        -f)

            COMPREPLY=($( compgen -W 'chomp chop chr crypt hex index lc \

	    lcfirst length oct ord pack q qq reverse rindex sprintf \

	    substr tr uc ucfirst y m pos quotemeta s split study qr abs \

	    atan2 cos exp hex int log oct rand sin sqrt srand pop push \

	    shift splice unshift grep join map qw reverse sort unpack \

	    delete each exists keys values binmode close closedir \

	    dbmclose dbmopen die eof fileno flock format getc print \

	    printf read readdir rewinddir seek seekdir select syscall \

	    sysread sysseek syswrite tell telldir truncate warn write \

	    pack read syscall sysread syswrite unpack vec -X chdir chmod \

	    chown chroot fcntl glob ioctl link lstat mkdir open opendir \

	    readlink rename rmdir stat symlink umask unlink utime caller \

	    continue do dump eval exit goto last next redo return \

	    sub wantarray caller import local my our package use defined \

	    formline reset scalar undef \

	    alarm exec fork getpgrp getppid getpriority kill pipe qx \

	    setpgrp setpriority sleep system times wait waitpid \

	    import no package require use bless dbmclose dbmopen package \

	    ref tie tied untie use accept bind connect getpeername \

	    getsockname getsockopt listen recv send setsockopt shutdown \

	    socket socketpair msgctl msgget msgrcv msgsnd semctl semget \

	    semop shmctl shmget shmread shmwrite endgrent endhostent \

	    endnetent endpwent getgrent getgrgid getgrnam getlogin \

	    getpwent getpwnam getpwuid setgrent setpwent endprotoent \

	    endservent gethostbyaddr gethostbyname gethostent \

	    getnetbyaddr getnetbyname getnetent getprotobyname \

	    getprotobynumber getprotoent getservbyname getservbyport \

	    getservent sethostent setnetent setprotoent setservent \

	    gmtime localtime time times' -- $cur ));

            return 0

        ;;

    esac;

    case $cur in 

        -*)

            COMPREPLY=($( compgen -W '-h -v -t -u -m -l -F -X -f -q' -- $cur ));

            return 0

        ;;

        */*)

            return 0

        ;;

        *)

            _perlmodules;

            COMPREPLY=(${COMPREPLY[@]} $( compgen -W '$( PAGER=cat man perl 2>/dev/null | sed -ne "/perl.*Perl overview/,/perlwin32/s/^[^a-z0-9]*\([a-z0-9]*\).*$/\1/p")' -- $cur ));

            return 0

        ;;

    esac

}

_perlmodules () 

{ 

    COMPREPLY=($( compgen -P "$prefix" -W "$( perl -e 'sub mods { my ($base,$dir)=@_; return if  $base !~ /^\Q$ENV{cur}/; chdir($dir) or return; for (glob(q[*.pm])) {s/\.pm$//; print qq[$base$_\n]}; mods(/^(?:[.\d]+|$Config{archname}-$Config{osname}|auto)$/ ? undef : qq[${base}${_}\\\\:\\\\:],qq[$dir/$_]) for grep {-d} glob(q[*]); } mods(undef,$_) for @INC;' )" -- $cur ))

}

_pgids () 

{ 

    COMPREPLY=($( compgen -W '$( command ps axo pgid | sed 1d )' -- $cur ))

}

_pgrep () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    COMPREPLY=($( compgen -W '$( command ps axo command | \

		      sed -ne "1d; s/^\[\?\([^-][^] ]*\).*$/\1/p" | \

		      sed -e "s/.*\///" )' -- $cur ));

    return 0

}

_pids () 

{ 

    COMPREPLY=($( compgen -W '$( command ps axo pid | sed 1d )' -- $cur ))

}

_pkg_config () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( compgen -W '-version --modversion \

		      --atleast-pkgconfig-version= --libs --libs-only-l \

		      --libs-only-other --libs-only-L --cflags \

		      --cflags-only-I --cflags-only-other --variable= \

		      --define-variable= --exists --uninstalled \

		      --atleast-version= --exact-version= --max-version= \

		      --list-all --debug --print-errors --silence-errors \

		      --errors-to-stdout -? --help --usage' -- $cur));

    else

        COMPREPLY=($( pkg-config --list-all 2>/dev/null | 				    awk '{print $1}' | grep "^$cur" ));

    fi

}

_poff () 

{ 

    local prev cur conns;

    [ -r /etc/ppp/peers/ ] || return 0;

    COMPREPLY=();

    prev=${COMP_WORDS[COMP_CWORD-1]};

    cur=${COMP_WORDS[COMP_CWORD]};

    conns=$(\ls --color=none /etc/ppp/peers | egrep -v '(\.bak|~)$');

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($(compgen -W '-r -d -c -a -h -v' -- $cur));

        return 0;

    fi;

    if [ $COMP_CWORD -eq 1 ] && [[ "$cur" != -* ]] || [[ "$prev" == -* ]]; then

        COMPREPLY=($(compgen -o filenames -W "$conns" $cur));

    fi;

    return 0

}

_pon () 

{ 

    local cur conns;

    [ -r /etc/ppp/peers/ ] || return 0;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    conns=$(\ls --color=none /etc/ppp/peers | egrep -v '(\.bak|~)$');

    if [ $COMP_CWORD -eq 1 ]; then

        COMPREPLY=($(compgen -o filenames -W "$conns" $cur));

    fi;

    return 0

}

_python () 

{ 

    local prev cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]##*/};

    case "$prev" in 

        -Q)

            COMPREPLY=($( compgen -W "old new warn warnall" -- $cur ));

            return 0

        ;;

        -W)

            COMPREPLY=($( compgen -W "ignore default all module once error" -- $cur ));

            return 0

        ;;

        -c)

            _filedir '@(py|pyc|pyo)';

            return 0

        ;;

        !(python|-?))

            [[ ${COMP_WORDS[COMP_CWORD-2]} != -@(Q|W) ]] && _filedir

        ;;

    esac;

    for ((i=0; i < ${#COMP_WORDS[@]}-1; i++ ))

    do

        if [[ ${COMP_WORDS[i]} == -c ]]; then

            _filedir;

        fi;

    done;

    if [[ "$cur" != -* ]]; then

        _filedir '@(py|pyc|pyo)';

    else

        COMPREPLY=($( compgen -W "- -d -E -h -i -O -Q -S -t -u 					   -U -v -V -W -x -c" -- $cur ));

    fi;

    return 0

}

_renice () 

{ 

    local command cur curopt i;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    command=$1;

    i=0;

    while [ $i -le $COMP_CWORD -a ${#COMPREPLY[@]} -eq 0 ]; do

        curopt=${COMP_WORDS[COMP_CWORD-$i]};

        case "$curopt" in 

            -u)

                COMPREPLY=($( compgen -u -- $cur ))

            ;;

            -g)

                _pgids

            ;;

            -p | $command)

                _pids

            ;;

        esac;

        i=$(( ++i ));

    done

}

_rl_enabled () 

{ 

    [[ "$( bind -v )" = *$1+([[:space:]])on* ]]

}

_rmmod () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    COMPREPLY=($( /sbin/lsmod | 		  awk '{if (NR != 1 && $1 ~ /^'$cur'/) print $1}' 2>/dev/null ));

    return 0

}

_root_command () 

{ 

    PATH=$PATH:/sbin:/usr/sbin:/usr/local/sbin _command $1 $2 $3

}

_route () 

{ 

    local cur prev;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    if [ "$prev" = dev ]; then

        COMPREPLY=($( ifconfig -a | sed -ne 's|^\('$cur'[^ ]*\).*$|\1|p' ));

        return 0;

    fi;

    COMPREPLY=($( compgen -W 'add del -host -net netmask metric mss \

				   window irtt reject mod dyn reinstate dev \

				   default gw' -- $cur ));

    COMPREPLY=($( echo " ${COMP_WORDS[@]}" | 		       (while read -d ' ' i; do

			   [ "$i" == "" ] && continue

			   # flatten array with spaces on either side,

			   # otherwise we cannot grep on word

			   # boundaries of first and last word

			   COMPREPLY=" ${COMPREPLY[@]} "

			   # remove word from list of completions

			   COMPREPLY=( ${COMPREPLY/ $i / } )

			done

		       echo ${COMPREPLY[@]})

		  ));

    return 0

}

_rsync () 

{ 

    local cur prev shell i userhost path;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    _expand || return 0;

    case "$prev" in 

        --@(config|password-file|include-from|exclude-from))

            _filedir;

            return 0

        ;;

        -@(T|-temp-dir|-compare-dest))

            _filedir -d;

            return 0

        ;;

        -@(e|-rsh))

            COMPREPLY=($( compgen -W 'rsh ssh' -- $cur ));

            return 0

        ;;

    esac;

    case "$cur" in 

        -*)

            COMPREPLY=($( compgen -W '-v -q  -c -a -r -R -b -u -l -L -H \

				-p -o -g -D -t -S -n -W -x -B -e -C -I -T -P \

				-z -h -4 -6 --verbose --quiet --checksum \

				--archive --recursive --relative --backup \

				--backup-dir --suffix= --update --links \

				--copy-links --copy-unsafe-links --safe-links \

				--hard-links --perms --owner --group --devices\

				--times --sparse --dry-run --whole-file \

				--no-whole-file --one-file-system \

				--block-size= --rsh= --rsync-path= \

				--cvs-exclude --existing --ignore-existing \

				--delete --delete-excluded --delete-after \

				--ignore-errors --max-delete= --partial \

				--force --numeric-ids --timeout= \

				--ignore-times --size-only --modify-window= \

				--temp-dir= --compare-dest= --compress \

				--exclude= --exclude-from= --include= \

				--include-from= --version --daemon --no-detach\

				--address= --config= --port= --blocking-io \

				--no-blocking-io --stats --progress \

				--log-format= --password-file= --bwlimit= \

				--write-batch= --read-batch= --help' -- $cur ))

        ;;

        *:*)

            shell=rsh;

            for ((i=1; i < COMP_CWORD; i++ ))

            do

                if [[ "${COMP_WORDS[i]}" == -@(e|-rsh) ]]; then

                    shell=${COMP_WORDS[i+1]};

                    break;

                fi;

            done;

            if [[ "$shell" == ssh ]]; then

                cur=${cur/\\:/:};

                userhost=${cur%%?(\\):*};

                path=${cur#*:};

                path=${path//\\\\\\\\ / };

                if [ -z "$path" ]; then

                    path=$(ssh -o 'Batchmode yes' 					$userhost pwd 2>/dev/null);

                fi;

                COMPREPLY=($( ssh -o 'Batchmode yes' $userhost 				command ls -aF1d "$path*" 2>/dev/null | 				sed -e 's/ /\\\\\\\ /g' -e 's/[*@|=]$//g' 				-e 's/[^\/]$/& /g' ));

            fi

        ;;

        *)

            _known_hosts -c -a;

            _filedir

        ;;

    esac;

    return 0

}

_scp () 

{ 

    local cur userhost path;

    local IFS='	

';

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    _expand || return 0;

    if [[ "$cur" == *:* ]]; then

        cur=${cur/\\:/:};

        userhost=${cur%%?(\\):*};

        path=${cur#*:};

        path=${path//\\\\\\\\ / };

        if [ -z "$path" ]; then

            path=$(ssh -o 'Batchmode yes' $userhost pwd 2>/dev/null);

        fi;

        COMPREPLY=($( ssh -o 'Batchmode yes' $userhost 			       command ls -aF1d "$path*" 2>/dev/null | 			       sed -e "s/[][(){}<>\",:;^&!$&=?\`|\\ ']/\\\\\\\\\\\\&/g" 				   -e 's/[*@|=]$//g' -e 's/[^\/]$/& /g' ));

        return 0;

    fi;

    [[ "$cur" == */* ]] || _known_hosts -c -a;

    COMPREPLY=(${COMPREPLY[@]} $( command ls -aF1d $cur* 			    2>/dev/null | sed 			    -e "s/[][(){}<>\",:;^&!$&=?\`|\\ ']/\\\\&/g" 			    -e 's/[*@|=]$//g' -e 's/[^\/]$/& /g' ));

    return 0

}

_screen () 

{ 

    local cur prev preprev;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    [ "$COMP_CWORD" -ge 2 ] && preprev=${COMP_WORDS[COMP_CWORD-2]};

    if [ "$preprev" = "-d" -o "$preprev" = "-D" -a "$prev" = "-r" -o "$prev" = "-R" ]; then

        COMPREPLY=($( command screen -ls | 				sed -ne 's|^[''	'']\+\('$cur'[0-9]\+\.[^''	'']\+\).*$|\1|p' ));

    else

        case "$prev" in 

            -[rR])

                COMPREPLY=($( command screen -ls | 					sed -ne 's|^[''	'']\+\('$cur'[0-9]\+\.[^''	'']\+\).*Detached.*$|\1|p' ))

            ;;

            -[dDx])

                COMPREPLY=($( command screen -ls | 					sed -ne 's|^[''	'']\+\('$cur'[0-9]\+\.[^''	'']\+\).*Attached.*$|\1|p' ))

            ;;

            -s)

                COMPREPLY=($( grep ^${cur:-[^#]} /etc/shells ))

            ;;

            *)



            ;;

        esac;

    fi;

    return 0

}

_service () 

{ 

    local cur sysvdir;

    COMPREPLY=();

    prev=${COMP_WORDS[COMP_CWORD-1]};

    cur=${COMP_WORDS[COMP_CWORD]};

    [[ ${COMP_WORDS[0]} != @(*init.d/!(functions|~)|service) ]] && return 0;

    [ $COMP_CWORD -gt 2 ] && return 0;

    [ -d /etc/rc.d/init.d ] && sysvdir=/etc/rc.d/init.d || sysvdir=/etc/init.d;

    if [[ $COMP_CWORD -eq 1 ]] && [[ $prev == "service" ]]; then

        _services;

    else

        COMPREPLY=($( compgen -W '`sed -ne "y/|/ /; \

				s/^.*Usage.*{\(.*\)}.*$/\1/p" \

				$sysvdir/${prev##*/} 2>/dev/null`' -- $cur ));

    fi;

    return 0

}

_services () 

{ 

    local sysvdir famdir;

    [ -d /etc/rc.d/init.d ] && sysvdir=/etc/rc.d/init.d || sysvdir=/etc/init.d;

    famdir=/etc/xinetd.d;

    COMPREPLY=($( builtin echo $sysvdir/!(*.rpmsave|*.rpmorig|*~|functions)));

    if [ -d $famdir ]; then

        COMPREPLY=(${COMPREPLY[@]} $( builtin echo $famdir/!(*.rpmsave|*.rpmorig|*~)));

    fi;

    COMPREPLY=($( compgen -W '${COMPREPLY[@]#@($sysvdir|$famdir)/}' -- $cur ))

}

_signals () 

{ 

    local i;

    COMPREPLY=($( compgen -A signal SIG${cur#-} ));

    for ((i=0; i < ${#COMPREPLY[@]}; i++ ))

    do

        COMPREPLY[i]=-${COMPREPLY[i]#SIG};

    done

}

_ssh () 

{ 

    local cur prev;

    local -a config;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case "$prev" in 

        -*c)

            COMPREPLY=($( compgen -W 'blowfish 3des 3des-cbc blowfish-cbc \

			   arcfour cast128-cbc' -- $cur ))

        ;;

        -*i)

            _filedir

        ;;

        -*l)

            COMPREPLY=($( compgen -u -- $cur ))

        ;;

        *)

            _known_hosts -a;

            [ $COMP_CWORD -eq 1 ] || COMPREPLY=(${COMPREPLY[@]} $( compgen -c -- $cur ))

        ;;

    esac;

    return 0

}

_sysctl () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    COMPREPLY=($( compgen -W "$(sysctl -N -a 2>/dev/null)" -- $cur ));

    return 0

}

_tar () 

{ 

    local cur ext regex tar untar;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    if [ $COMP_CWORD -eq 1 ]; then

        COMPREPLY=($( compgen -W 'c t x u r d A' -- $cur ));

        return 0;

    fi;

    case "${COMP_WORDS[1]}" in 

        ?(-)c*f)

            _filedir;

            return 0

        ;;

        +([^IZzjy])f)

            ext='t@(ar?(.@(Z|gz|bz?(2)))|gz|bz?(2))';

            regex='t\(ar\(\.\(Z\|gz\|bz2\?\)\)\?\|gz\|bz2\?\)'

        ;;

        *[Zz]*f)

            ext='t?(ar.)@(gz|Z)';

            regex='t\(ar\.\)\?\(gz\|Z\)'

        ;;

        *[Ijy]*f)

            ext='t?(ar.)bz?(2)';

            regex='t\(ar\.\)\?bz2\?'

        ;;

        *)

            _filedir;

            return 0

        ;;

    esac;

    if [[ "$COMP_LINE" == *$ext' ' ]]; then

        tar=$( echo "$COMP_LINE" | 			sed -e 's/^.* \([^ ]*'$regex'\) .*$/\1/' );

        untar=t${COMP_WORDS[1]//[^Izjyf]/};

        COMPREPLY=($( compgen -W "$( echo $( tar $untar $tar 				2>/dev/null ) )" -- "$cur" ));

        return 0;

    fi;

    _filedir $ext;

    return 0

}

_tcpdump () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case "$prev" in 

        -@(r|w|F))

            _filedir;

            return 0

        ;;

        -i)

            _available_interfaces -a;

            return 0

        ;;

    esac;

    if [[ "$cur" == -* ]]; then

        COMPREPLY=($( compgen -W '-a -d -e -f -l -n -N -O -p \

			-q -R -S -t -u -v -x -C -F -i -m -r -s -T -w \

			-E' -- $cur ));

    fi

}

_uids () 

{ 

    if type getent >&/dev/null; then

        COMPREPLY=($( getent passwd | 			    awk -F: '{if ($3 ~ /^'$cur'/) print $3}' ));

    else

        if type perl >&/dev/null; then

            COMPREPLY=($( compgen -W '$( perl -e '"'"'while (($uid) = (getpwent)[2]) { print $uid . "\n" }'"'"' )' -- $cur ));

        else

            COMPREPLY=($( awk 'BEGIN {FS=":"} {if ($3 ~ /^'$cur'/) print $3}'			    /etc/passwd ));

        fi;

    fi

}

_umount () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    COMPREPLY=($( compgen -W '$( mount | cut -d" " -f 3 )' -- $cur ));

    return 0

}

_update_alternatives () 

{ 

    local cur prev mode args i;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case "$prev" in 

        --@(altdir|admindir))

            _filedir -d;

            return 0

        ;;

        --@(help|version))

            return 0

        ;;

    esac;

    for ((i=1; i < COMP_CWORD; i++ ))

    do

        if [[ "${COMP_WORDS[i]}" == --@(install|remove|auto|display|config) ]]; then

            mode=${COMP_WORDS[i]};

            args=$(($COMP_CWORD - i));

            break;

        fi;

    done;

    case $mode in 

        --install)

            case $args in 

                1)

                    _filedir

                ;;

                2)

                    installed_alternatives

                ;;

                3)

                    _filedir

                ;;

            esac

        ;;

        --remove)

            case $args in 

                1)

                    installed_alternatives

                ;;

                2)

                    _filedir

                ;;

            esac

        ;;

        --auto)

            installed_alternatives

        ;;

        --display)

            installed_alternatives

        ;;

        --config)

            installed_alternatives

        ;;

        *)

            COMPREPLY=($( compgen -W '--verbose --quiet --help --version \

			       --altdir --admindir' -- $cur ) $( compgen -W '--install --remove --auto --display \

			       --config' -- $cur ))

        ;;

    esac

}

_update_rc_d () 

{ 

    local cur prev sysvdir services options valid_options;

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    [ -d /etc/rc.d/init.d ] && sysvdir=/etc/rc.d/init.d || sysvdir=/etc/init.d;

    services=($(echo $sysvdir/!(README*|*.sh|*.dpkg*|*.rpm*)));

    services=(${services[@]#$sysvdir/});

    options=(-f -n);

    if [[ $COMP_CWORD -eq 1 || "$prev" == -* ]]; then

        valid_options=($( 	    echo "${COMP_WORDS[@]} ${options[@]}" 	    | tr " " "\n" 	    | sed -ne "/$( echo "${options[@]}" | sed "s/ /\\|/g" )/p" 	    | sort | uniq -u 	    ));

        COMPREPLY=($( compgen -W '${options[@]} ${services[@]}' 	    -X '$( echo ${COMP_WORDS[@]} | tr " " "|" )' -- $cur ));

    else

        if [[ "$prev" == ?($( echo ${services[@]} | tr " " "|" )) ]]; then

            COMPREPLY=($( compgen -W 'remove defaults start stop' -- $cur ));

        else

            if [[ "$prev" == defaults && "$cur" == [0-9] ]]; then

                COMPREPLY=(0 1 2 3 4 5 6 7 8 9);

            else

                if [[ "$prev" == defaults && "$cur" == [sk]?([0-9]) ]]; then

                    COMPREPLY=(0 1 2 3 4 5 6 7 8 9);

                else

                    if [[ "$prev" == defaults && -z "$cur" ]]; then

                        COMPREPLY=(0 1 2 3 4 5 6 7 8 9 s k);

                    else

                        if [[ "$prev" == ?(start|stop) ]]; then

                            if [[ "$cur" == [0-9] || -z "$cur" ]]; then

                                COMPREPLY=(0 1 2 3 4 5 6 7 8 9);

                            else

                                if [[ "$cur" == [0-9][0-9] ]]; then

                                    COMPREPLY=($cur);

                                else

                                    COMPREPLY=();

                                fi;

                            fi;

                        else

                            if [[ "$prev" == ?([0-9][0-9]|[0-6S]) ]]; then

                                if [[ -z "$cur" ]]; then

                                    if [[ $prev == [0-9][0-9] ]]; then

                                        COMPREPLY=(0 1 2 3 4 5 6 S);

                                    else

                                        COMPREPLY=(0 1 2 3 4 5 6 S .);

                                    fi;

                                else

                                    if [[ "$cur" == [0-6S.] ]]; then

                                        COMPREPLY=($cur);

                                    else

                                        COMPREPLY=();

                                    fi;

                                fi;

                            else

                                if [[ "$prev" == "." ]]; then

                                    COMPREPLY=($(compgen -W "start stop" -- $cur));

                                else

                                    COMPREPLY=();

                                fi;

                            fi;

                        fi;

                    fi;

                fi;

            fi;

        fi;

    fi;

    return 0

}

_user_at_host () 

{ 

    local cur;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    if [[ $cur == *@* ]]; then

        _known_hosts;

    else

        COMPREPLY=($( compgen -u -- "$cur" ));

    fi;

    return 0

}

_usergroup () 

{ 

    local IFS='

';

    cur=${cur//\\\\ / };

    if [[ $cur = *@(\\:|.)* ]] && [ -n "$bash205" ]; then

        user=${cur%%*([^:.])};

        COMPREPLY=($(compgen -P ${user/\\\\} -g -- ${cur##*[.:]}));

    else

        if [[ $cur = *:* ]] && [ -n "$bash205" ]; then

            COMPREPLY=($( compgen -g -- ${cur##*[.:]} ));

        else

            COMPREPLY=($( compgen -S : -u -- $cur ));

        fi;

    fi

}

_vncviewer () 

{ 

    local cur prev;

    local -a config;

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case "$prev" in 

        -via)

            _known_hosts -a

        ;;

        *)

            COMPREPLY=($( ssh -o 'Batchmode yes' $prev 			  "ping -bnc 4 255.255.255.255" 2>/dev/null | 			  awk -F ' ' '{print $4}' | 			  sort -n | uniq | egrep '[0-9]+\.[0-9]+\.' 2>/dev/null ))

        ;;

    esac;

    return 0

}

_wvdial () 

{ 

    local cur prev config i IFS='	

';

    COMPREPLY=();

    cur=${COMP_WORDS[COMP_CWORD]};

    prev=${COMP_WORDS[COMP_CWORD-1]};

    case $prev in 

        --config)

            _filedir;

            return 0

        ;;

    esac;

    case $cur in 

        -*)

            COMPREPLY=($( compgen -W '--config --chat \

				--remotename --help --version --no-syslog' 				-- $cur ))

        ;;

        *)

            config="/etc/wvdial.conf"'	'"$HOME/.wvdialrc";

            for ((i=1; i < COMP_CWORD; i++ ))

            do

                if [[ "${COMP_WORDS[i]}" == "--config" ]]; then

                    config=${COMP_WORDS[i+1]};

                    break;

                fi;

            done;

            COMPREPLY=($( sed -ne 				    "s|^\[Dialer \($cur.*\)\]$|\1|p" 				    $config 2>/dev/null |grep -v '^Defaults$'));

            COMPREPLY=${COMPREPLY// /\\ }

        ;;

    esac

}

command_not_found_handle () 

{ 

    /usr/bin/python /usr/lib/command-not-found -- $1;

    return $?

}

installed_alternatives () 

{ 

    local admindir;

    for i in alternatives dpkg/alternatives rpm/alternatives;

    do

        [ -d /var/lib/$i ] && admindir=/var/lib/$i && break;

    done;

    for ((i=1; i < COMP_CWORD; i++ ))

    do

        if [[ "${COMP_WORDS[i]}" == --admindir ]]; then

            admindir=${COMP_WORDS[i+1]};

            break;

        fi;

    done;

    COMPREPLY=($( command ls $admindir | grep "^$cur" ))

}

```

Why would it output all that other stuff? On my older version (Ubuntu 6), all I got were the environment variables at the top.

Any hints?

PS: I'm a Linux noob, so try to make any answers uncomplicated.

Edit: i also found it to happen when I type "declare" with no arguments.

---

### Post by firestarsolo on 2007-12-02
Bump for great justice . . .

---

### Post by 1longtime on 2008-01-09
Bump, same issue here... huge amount of output when I type "set" at the command line.

---

