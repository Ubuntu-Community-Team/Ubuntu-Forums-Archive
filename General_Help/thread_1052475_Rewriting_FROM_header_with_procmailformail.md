---
title: "Rewriting FROM header with procmail/formail"
date: 2009-01-27
forum: General Help
---

### Post by llamakc on 2009-01-27
I'm a Mutt user that has Postfix running on a vanity server. I currently use procmail to filter out spam (via spamassassin), and to deliver my mail. 

I can filter out a specific subset of messages that I want forwarded to my cellphone via a text message. I need help with getting the forwarded email to **RETAIN THE ORIGINAL FROM ADDRESS** instead of my vanity server (that forwards the email). This currently works (partially) with:

```

:0 fhw
FROM=|$FORMAIL -rtzx From:
{
:0 c
! XXXXXXXXXX@vtext.com
}

```Where the XXXXXXXXXX is my cell number. I'm aware that this recipe is FUBAR, as I receive these errors in my procmail.log:

```

procmail: Executing "-rtzxFrom:"
/bin/sh: -z: invalid option
Usage:    /bin/sh [GNU long option] [option] ...
    /bin/sh [GNU long option] [option] script-file ...
GNU long options:
    --debug
    --debugger
    --dump-po-strings
    --dump-strings
    --help
    --init-file
    --login
    --noediting
    --noprofile
    --norc
    --posix
    --protected
    --rcfile
    --restricted
    --verbose
    --version
    --wordexp
Shell options:
    -irsD or -c command or -O shopt_option        (invocation only)
    -abefhkmnptuvxBCHP or -o option
procmail: Assigning "FROM="
procmail: Error while writing to "-rtzxFrom:"
procmail: Skipped "{"
...
procmail: Closing brace unexpected

```So I removed the "z" option, and this is the current warning in the log.

```

procmail: Executing "-rtx,From:"
/bin/sh: From:: No such file or directory
procmail: Assigning "FROM="
procmail: Error while writing to "-rtx"
procmail: Skipped "{"
...
procmail: Closing brace unexpected

```The above does forward certain emails to my phone, but does not retain the FROM header.

Where is my error? I have read the man page for formail and Googled for a recipe that will extract the original From address and rewrite the forwarded email, retaining the From address, and then forwarding it to my cellphone.

Ideas?

---

