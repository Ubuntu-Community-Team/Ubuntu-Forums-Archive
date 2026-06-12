---
title: "how to limit memory-hungriness ?"
date: 2005-05-02
forum: Desktop Environments
---

### Post by cudjoe on 2005-05-02
Yesterday I was watching a movie with gmplayer, when it suddenly froze (after 1hour or so). 
I took a quick look at system usage with "top", I saw that gmplayer was eating 75% of my 400MB of memory... gourmand ! but this doesn't seem to occur with consistency...

I was wondering if there would be a way to limit memory usage of a specific program, so that the system survives when multimedia softwares become so glutton ?

Could you tell me guyz what do you usually do to avoid such problems ?

Many Thanks

--
cudjoe

---

### Post by GrumpySmurf on 2005-05-02
[quote="cudjoe"]I was wondering if there would be a way to limit memory usage of a specific program, so that the system survives when multimedia softwares become so glutton ?

Could you tell me guyz what do you usually do to avoid such problems ?[/quote]
I haven't encountered problems with memory like that.  You may wish to look into the use of the ulimit command.  From the bash man page:

```
       ulimit [-SHacdflmnpstuv [limit]]
              Provides  control  over the resources available to the shell and
              to processes started by it, on systems that allow such  control.
              The -H and -S options specify that the hard or soft limit is set
              for the given resource.  A hard limit cannot be  increased  once
              it  is set; a soft limit may be increased up to the value of the
              hard limit.  If neither -H nor -S is specified,  both  the  soft
              and  hard limits are set.  The value of limit can be a number in
              the unit specified for the resource or one of the special values
              hard,  soft,  or  unlimited,  which  stand  for the current hard
              limit, the current soft limit, and no limit,  respectively.   If
              limit  is  omitted,  the  current value of the soft limit of the
              resource is printed, unless the -H option is given.   When  more
              than  one  resource  is  specified,  the limit name and unit are
              printed before the value.  Other options are interpreted as fol-
              lows:
              -a     All current limits are reported
              -c     The maximum size of core files created
              -d     The maximum size of a processâs data segment
              -f     The maximum size of files created by the shell
              -l     The maximum size that may be locked into memory
              -m     The maximum resident set size
              -n     The maximum number of open file descriptors (most systems
                     do not allow this value to be set)
              -p     The pipe size in 512-byte blocks (this may not be set)
              -s     The maximum stack size
              -t     The maximum amount of cpu time in seconds
              -u     The maximum number of processes  available  to  a  single
                     user
              -v     The  maximum  amount  of  virtual memory available to the
                     shell

              If limit is given, it is the new value of the specified resource
              (the -a option is display only).  If no option is given, then -f
              is assumed.  Values are in 1024-byte increments, except for  -t,
              which  is  in seconds, -p, which is in units of 512-byte blocks,
              and -n and -u, which are unscaled values.  The return status  is
              0  unless an invalid option or argument is supplied, or an error
              occurs while setting a new limit.

```
You will probably need to have the pam_limits.so module loaded by your PAM configuration.  See [http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/pam-6.html#ss6.12](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/pam-6.html#ss6.12) for more information about the pam_limits module, and [http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/pam.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/pam.html) for complete documentation on PAM.

---

### Post by cudjoe on 2005-05-09
many thanks ! I'll play with that ! All these little enhancements are really time consuming... and such problems are unfortunate ! I'm strongly advertising Linux and starting programs from command line makes my flatmates shiver ! especially for watching a movie !

---

