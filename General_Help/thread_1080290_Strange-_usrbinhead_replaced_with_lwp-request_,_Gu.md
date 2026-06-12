---
title: "Strange- /usr/bin/head replaced with lwp-request , Gutsy Server"
date: 2009-02-25
forum: General Help
---

### Post by sp00n on 2009-02-25
Bizzarely, lots of my scripts have stopped working, and output "head: unknown option -n". Now I am certain that head has a -n option. Executing /usr/bin/head gives the following output: ```
Usage: head [-options] <url>...
    -m <method>   use method for the request (default is 'HEAD')
    -f            make request even if head believes method is illegal
    -b <base>     Use the specified URL as base
    -t <timeout>  Set timeout value
    -i <time>     Set the If-Modified-Since header on the request
    -c <conttype> use this content-type for POST, PUT, CHECKIN
    -a            Use text mode for content I/O
    -p <proxyurl> use this as a proxy
    -P            don't load proxy settings from environment
    -H <header>   send this HTTP header (you can specify several)
    -C <username>:<password>
                  provide credentials for basic authentication

    -u            Display method and URL before any response
    -U            Display request headers (implies -u)
    -s            Display response status code
    -S            Display response status chain
    -e            Display response headers
    -d            Do not display content
    -o <format>   Process HTML content in various ways

    -v            Show program version
    -h            Print this message

    -x            Extra debugging output

```

So I execute /usr/bin/head -v, ang get the following:

```
This is lwp-request version 2.08 (libwww-perl-5.808)

Copyright 1995-1999, Gisle Aas.

This program is free software; you can redistribute it and/or
modify it under the same terms as Perl itself.

```

Surely this cant be right!

I have another server running Gutsy Server, so I can copy the original file across. But how on earth would this have happened? How would I replace this file if I did not have access to another gutsy server?

---

### Post by wowbagger53 on 2009-02-25
Hmmm....

/usr/bin/HEAD (upper case) is a symlink to lwp-request on my intrepid.

Is this a clue?

---

### Post by sp00n on 2009-02-25
Hey - thanks for the quick reply.

interesting - /usr/bin/POST is a symlink to lwp-request. I'm guessing that is the same for you. Also standard symlinks such as usr/bin/gksudo -> gksu are present. Perhaps whatever it was that configured the lwp-request symlinks had a typo, replacing /usr/bin/head instead of creating the symlink /usr/bin/HEAD? Very odd. I have executed ```
 sudo ln -s lwp-request HEAD

``` to replace the HEAD symlink in case anything else was looking for it.

Anybody know if i can replace head with apt or synaptic or dpkg?

---

### Post by wowbagger53 on 2009-02-25
I believe /usr/bin/head is in package coreutils.

Don't ask me how it got screwed up. Perhaps some case-insensitive something-or-other?

---

