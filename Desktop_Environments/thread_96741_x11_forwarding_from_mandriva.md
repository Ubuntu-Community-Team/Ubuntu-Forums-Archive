---
title: "x11 forwarding from mandriva?"
date: 2005-11-29
forum: Desktop Environments
---

### Post by zilla1126 on 2005-11-29
Previously in Mandr* I was able to ssh into another Mandr* server and then (without doing anything different) run GUI programs on that remote machine and have them come up on my end.

Right now I am logged into a Mandr* server from my Ubuntu 5.10 machine and this does not happen.  I think I have checked everything out...

Here are some configs:

sshd:

#Port 22
#Protocol 2,1
Protocol 2
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

# HostKey for protocol version 1
HostKey /etc/ssh/ssh_host_key
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key

# Lifetime and size of ephemeral version 1 server key
#KeyRegenerationInterval 1h
#ServerKeyBits 768

# Logging
# obsoletes QuietMode and FascistLogging
#SyslogFacility AUTH
#LogLevel INFO

# Authentication:

#LoginGraceTime 2m
PermitRootLogin yes
#StrictModes yes
#MaxAuthTries 6

#RSAAuthentication yes
#PubkeyAuthentication yes
#AuthorizedKeysFile     .ssh/authorized_keys

#RhostsRSAAuthentication no
# similar for protocol version 2
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# RhostsRSAAuthentication and HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes

# To disable tunneled clear text passwords, change to no here!
#PasswordAuthentication yes
#PermitEmptyPasswords no

# Change to no to disable s/key passwords
#ChallengeResponseAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication mechanism.
# Depending on your PAM configuration, this may bypass the setting of
# PasswordAuthentication, PermitEmptyPasswords, and
# "PermitRootLogin without-password". If you just want the PAM account and
# session checks to run without PAM authentication, then enable this but set
# ChallengeResponseAuthentication=no
UsePAM no

AllowTcpForwarding yes
#GatewayPorts no
X11Forwarding yes
X11DisplayOffset 10#PrintLastLog yes
#TCPKeepAlive yes
#UseLogin no
UsePrivilegeSeparation yes
#PermitUserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS yes
#PidFile /var/run/sshd.pid
#MaxStartups 10

# no default banner path
#Banner /some/path

# override default of no subsystems
Subsystem       sftp    /usr/lib/ssh/sftp-server

X11UseLocalhost yes
#PrintMotd yes# .bashrc

# User specific aliases and functions

# Source global definitions
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi


/root/.bashrc:
# .bashrc

PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/X11R6/bin:/usr/local/bin:/usr/local/sbin
ENV=$HOME/.bashrc
USERNAME="root"
export USERNAME ENV PATH

# Source global definitions
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi


/etc/bashrc:

# /etc/bashrc

# System wide functions and aliases
# Environment stuff goes in /etc/profile

# by default, we want this to get set.
# Even for non-interactive, non-login shells.
if [ "`id -gn`" = "`id -un`" -a `id -u` -gt 99 ]; then
        umask 002
else
        umask 022
fi

# are we an interactive shell?
if [ "$PS1" ]; then
    case $TERM in
        xterm*)
            PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
            ;;
        *)
            ;;
    esac
    [ "$PS1" = "\\s-\\v\\\$ " ] && PS1="[\u@\h \W]\\$ "

    if [ -z "$loginsh" ]; then # We're not a login shell
        # Not all scripts in profile.d are compatible with other shells
        # TODO: make the scripts compatible or check the running shell by
        # themselves.
        if [ -n "${BASH_VERSION}${KSH_VERSION}${ZSH_VERSION}" ]; then
            for i in /etc/profile.d/*.sh; do
                if [ -x $i ]; then
                    . $i
                fi
            done
        fi
    fi
fi
[ -z $XAUTHORITY ] && export XAUTHORITY=$HOME/.Xauthority
unset loginsh

#PrintLastLog yes
#TCPKeepAlive yes


/etc/skel/.bashrc:

---

### Post by cwaldbieser on 2005-11-29
> **zilla1126]Previously in Mandr* I was able to ssh into another Mandr* server and then (without doing anything different) run GUI programs on that remote machine and have them come up on my end.

Right now I am logged into a Mandr* server from my Ubuntu 5.10 machine and this does not happen.  I think I have checked everything out...

Here are some configs:

sshd:

#Port 22
#Protocol 2,1
Protocol 2
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

# HostKey for protocol version 1
HostKey /etc/ssh/ssh_host_key
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key

# Lifetime and size of ephemeral version 1 server key
#KeyRegenerationInterval 1h
#ServerKeyBits 768

# Logging
# obsoletes QuietMode and FascistLogging
#SyslogFacility AUTH
#LogLevel INFO

# Authentication:

#LoginGraceTime 2m
PermitRootLogin yes
#StrictModes yes
#MaxAuthTries 6

#RSAAuthentication yes
#PubkeyAuthentication yes
#AuthorizedKeysFile     .ssh/authorized_keys

#RhostsRSAAuthentication no
# similar for protocol version 2
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# RhostsRSAAuthentication and HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes

# To disable tunneled clear text passwords, change to no here!
#PasswordAuthentication yes
#PermitEmptyPasswords no

# Change to no to disable s/key passwords
#ChallengeResponseAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication mechanism.
# Depending on your PAM configuration, this may bypass the setting of
# PasswordAuthentication, PermitEmptyPasswords, and
# "PermitRootLogin without-password". If you just want the PAM account and
# session checks to run without PAM authentication, then enable this but set
# ChallengeResponseAuthentication=no
UsePAM no

AllowTcpForwarding yes
#GatewayPorts no
X11Forwarding yes
X11DisplayOffset 10#PrintLastLog yes
#TCPKeepAlive yes
#UseLogin no
UsePrivilegeSeparation yes
#PermitUserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS yes
#PidFile /var/run/sshd.pid
#MaxStartups 10

# no default banner path
#Banner /some/path

# override default of no subsystems
Subsystem       sftp    /usr/lib/ssh/sftp-server

X11UseLocalhost yes
#PrintMotd yes# .bashrc

# User specific aliases and functions

# Source global definitions
if [ -f /etc/bashrc ] said:**
> ; then
        . /etc/bashrc
fi


/etc/bashrc:

# /etc/bashrc

# System wide functions and aliases
# Environment stuff goes in /etc/profile

# by default, we want this to get set.
# Even for non-interactive, non-login shells.
if [ "`id -gn`" = "`id -un`" -a `id -u` -gt 99 ]; then
        umask 002
else
        umask 022
fi

# are we an interactive shell?
if [ "$PS1" ]; then
    case $TERM in
        xterm*)
            PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
            ;;
        *)
            ;;
    esac
    [ "$PS1" = "\\s-\\v\\\$ " ] && PS1="[\u@\h \W]\\$ "

    if [ -z "$loginsh" ]; then # We're not a login shell
        # Not all scripts in profile.d are compatible with other shells
        # TODO: make the scripts compatible or check the running shell by
        # themselves.
        if [ -n "${BASH_VERSION}${KSH_VERSION}${ZSH_VERSION}" ]; then
            for i in /etc/profile.d/*.sh; do
                if [ -x $i ]; then
                    . $i
                fi
            done
        fi
    fi
fi
[ -z $XAUTHORITY ] && export XAUTHORITY=$HOME/.Xauthority
unset loginsh

#PrintLastLog yes
#TCPKeepAlive yes


/etc/skel/.bashrc:

What is the command (with options) you are using to connect?

---

### Post by zilla1126 on 2005-11-29
>>What is the command (with options) you are using to connect?

ssh [email]root@www.mysite.com[/email]

I also tried 

ssh -X [email]root@www.mysite.com[/email]

---

### Post by cwaldbieser on 2005-11-29
[QUOTE=zilla1126]>>What is the command (with options) you are using to connect?

ssh [email]root@www.mysite.com[/email]

I also tried 

ssh -X [email]root@www.mysite.com[/email][/QUOTE]

What about if you 
```

$ ssh -Y -l user server

```
What does the remote DISPLAY environment variable get set to?

---

### Post by zilla1126 on 2005-11-30
>>What does the remote DISPLAY environment variable get set to?

I have no idea, but the command you gave worked perfectly.  Mandr* must have that as a alias/default or something.  They do things like that; like updatedb is the same as slocate -u.

Thanks for your help.

---

### Post by cwaldbieser on 2005-11-30
[QUOTE=zilla1126]>>What does the remote DISPLAY environment variable get set to?

I have no idea, but the command you gave worked perfectly.  Mandr* must have that as a alias/default or something.  They do things like that; like updatedb is the same as slocate -u.

Thanks for your help.[/QUOTE]
The -Y option is for secure X forwarding.  I guess your server is just configured to reject insecure X forwarding.

If you ever need to figure out your DISPLAY, you can just 
```

$ echo $DISPLAY
:0.0

```
The above result is typical for the local display.

---

