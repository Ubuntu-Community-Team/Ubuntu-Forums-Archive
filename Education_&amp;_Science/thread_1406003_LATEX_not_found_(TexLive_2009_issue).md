---
title: "LATEX not found (TexLive 2009 issue)"
date: 2010-02-13
forum: Education &amp; Science
---

### Post by AmadeusOK on 2010-02-13
When I was trying to install AUCTeX 11.85 the configuration process aborted because LATeX was not found:

```

checking for latex... NONE
configure: error: LaTeX not found, aborting!
You must install LaTeX for preview to work.
configure: error: ./configure failed for preview

``` 

I have no idea what the problem is. I just installed TexLive 2009 a few days ago. After the installation I added a few lines to my /etc/environment file. So it looks like this:

```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
PATH="/usr/local/texlive/2009/bin/x86_64-linux"
MANPATH="/usr/local/texlive/2009/texmf/doc/man"
INFOPATH="usr/local/texlive/2009/texmf/doc/info"
export PATH
```

Is that correct? Can anyone help me? Thanks.

---

### Post by Abdus on 2010-02-14
> **AmadeusOK said:**
> When I was trying to install AUCTeX 11.85 the configuration process aborted because LATeX was not found:

```

checking for latex... NONE
configure: error: LaTeX not found, aborting!
You must install LaTeX for preview to work.
configure: error: ./configure failed for preview

``` 

I have no idea what the problem is. I just installed TexLive 2009 a few days ago. After the installation I added a few lines to my /etc/environment file. So it looks like this:

```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
PATH="/usr/local/texlive/2009/bin/x86_64-linux"
MANPATH="/usr/local/texlive/2009/texmf/doc/man"
INFOPATH="usr/local/texlive/2009/texmf/doc/info"
export PATH
```

Is that correct? Can anyone help me? Thanks.

Your /etc/environment lacks the most important line for your system to recognize LaTeX presence - the path to TeXLive binaries. It should most probably look like this:
```
PATH="[COLOR="red"]/usr/local/texlive/2009/bin/x86_64-linux:[/COLOR]/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

EDIT: Seems adding it as the second line in your file didn't work, so I would move the contents of the second line to the first.

---

### Post by AmadeusOK on 2010-02-14
Hey Abdus,

Thank you very much. Yes, adding the directory to the PATH on the first line did the trick. So now I have AUCTeX 11.85 installed on my laptop.

---

