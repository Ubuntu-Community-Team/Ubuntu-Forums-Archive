---
title: "man -w"
date: 2006-06-12
forum: Desktop Environments
---

### Post by jjstautt on 2006-06-12
For some reason when I issue the command "man -w" in ubuntu 6.06 I get the response "What manual page do you want?" rather than a list of the locations of the man pages that I would expect. Has anyone else seen this or have a solution? Is this an ubuntu bug?

---

### Post by mcduck on 2006-06-12
you still need to tell man which manual's location you are looking for.

For example, 'man -w man'

---

### Post by jjstautt on 2006-06-12
[QUOTE=mcduck]you still need to tell man which manual's location you are looking for.

For example, 'man -w man'[/QUOTE]

hmm... ok. Thanks. I am migrating from Slackware 10.1, which the command worked in. I presume the functionality of man changed at some point??

I was trying to get the Intel Fortran compiler to work (which uses 'man -w' in its shell scripts that set your paths and such). The script does the following:

if [ -z "${MANPATH}" ]
then
    MANPATH="/usr/local/packages/intel/intel_fc_80/man":$(man -w); export MANPATH
else
    MANPATH="/usr/local/packages/intel/intel_fc_80/man:${MANPATH}"; export MANPATH
fi

What would be the best way to accomplish this without using "man -w"?

---

### Post by mcduck on 2006-06-14
> **jjstautt]hmm... ok. Thanks. I am migrating from Slackware 10.1, which the command worked in. I presume the functionality of man changed at some point??

I was trying to get the Intel Fortran compiler to work (which uses 'man -w' in its shell scripts that set your paths and such). The script does the following:

if [ -z "${MANPATH}" ]
then
    MANPATH="/usr/local/packages/intel/intel_fc_80/man":$(man -w) said:**
> 
I'm not sure, I'm not much of a coder. But doesn't 'manpath' command do exactly what you want?

[QUOTE=manpath manual page]manpath - determine search path for manual pages

If  $MANPATH  is  set,  manpath will simply display its contents and issue a warning. If not, manpath will determine a suitable manual page hierarchy search path and display the results.

---

### Post by jjstautt on 2006-08-21
> **mcduck said:**
> I'm not sure, I'm not much of a coder. But doesn't 'manpath' command do exactly what you want?

Yes, this would work if I test for the existence of manpath. The functionality for 'manpath' was provided in Slackware 10.1 with 'man -w'.

---

