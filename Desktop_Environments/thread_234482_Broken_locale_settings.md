---
title: "Broken locale settings"
date: 2006-08-11
forum: Desktop Environments
---

### Post by mssever on 2006-08-11
Since the Dapper repos contain an outdated version of BZFlag, I decided to use the version in Edgy. So, I did a find/replace in my sources.list and replaced dapper with edgy. I installed the current bzflag, which brought in a few dependencies (some C/C++ stuff if I remember correctly). I then switched my sources.list back to dapper.

Now, I'm having locale problems. gcontrol won't run at all (see [this thread]("http://www.ubuntuforums.org/showthread.php?t=225278")), and I get the following non-fatal errors from Synaptic:
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US.UTF-8",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory

```

Here's the output of locale:
```
~:$ locale
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LANGUAGE=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

How can I fix this? If I knew how to roll everything back to the way it was before upgrading bzflag, I'd do so. ](*,)

EDIT: I've re-installed my language packs, which seemed to cause man to stop complaining about the locale, but made no difference other than that.

---

### Post by mssever on 2006-08-15
bump

---

### Post by devilsadvocate1987 on 2006-08-17
i had the exact same problem. almost identical errors.
i took a hint from [http://www.howtoforge.com/perfect_xen_setup_debian_ubuntu_p4](http://www.howtoforge.com/perfect_xen_setup_debian_ubuntu_p4)

and did 
```
apt-get install localeconf
```

you are asked the following questions, reply to them as below: 

Manage locale configuration files with debconf? <-- Yes
Environment settings that should override the default locale: <-- do not select anything
Replace existing locale configuration files? <-- Yes
Default system locale: <-- e.g. en_US ISO-8859-1

(I wasn't asked the Default System Locale question)

apt-get upgrade seems to be running smoothly now. The full install isn't over yet, and a lot of packeages are yet to be configured, but its gone further and smoother than ever before.

hope this helps

---

### Post by mssever on 2006-08-17
[LEFT]Thanks for the info. Unfortunately, it didn't work for me. After some checking I believe that my problem is not with my locale settings but with my broken/buggy C libs. So, if I can figure out the verion number to roll back to, I think that that will solve my problem.
[/LEFT]

---

### Post by mlind on 2006-08-17
> 
locale: Cannot set LC_ALL to default locale: No such file or directory


If you reinstalled Dapper's language-pack-en (version 1:6.06+20060529), try reconfiguring locales
```

sudo dpkg-reconfigure locales

```

If you want Edgy's package for Dapper, you need to backport it (build against Dapper's libraries).

---

### Post by mssever on 2006-08-17
I've reinstalled every en language pack I could find, without success. dpkg-reconfigure locales didn't help, either. I think I''m going to have to change the versions of a bunch of libs. See [this thread]("http://ubuntuforums.org/showthread.php?t=238407").

How do you backport a package?

---

### Post by mlind on 2006-08-17
> **mssever said:**
> 
How do you backport a package?


You download the source package (from edgy repository) and build it on target distribution (dapper).

---

### Post by mssever on 2006-08-17
Do I need to do something special to ensure that the package I built is managable by apt?

---

### Post by mlind on 2006-08-17
> **mssever said:**
> Do I need to do something special to ensure that the package I built is managable by apt?

No, as long as you build it using debian packaging information.
There could be problems with build dependencies, but you should try it out.

---

### Post by mssever on 2006-08-17
I don't know anything about the debian packaging information. I'm used to compiling by doing ./configure --prefix=/foo/bar && make && sudo make install. What should I do differently? Or, is there a tutorial in this somewhere?

---

### Post by mlind on 2006-08-17
> **mssever said:**
> I don't know anything about the debian packaging information. I'm used to compiling by doing ./configure --prefix=/foo/bar && make && sudo make install. What should I do differently? Or, is there a tutorial in this somewhere?

I can help you with this if you want. I guess this goes offtopic, so you can send me a private message about this or make new thread about the subject somewhere.
Meanwhile, you can check out the links on my signature to get the hang of the process. Using pbuilder is probably the easiest and cleanest way to go.

---

