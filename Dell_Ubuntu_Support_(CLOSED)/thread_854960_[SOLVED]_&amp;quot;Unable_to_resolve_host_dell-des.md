---
title: "[SOLVED] &amp;quot;Unable to resolve host dell-desktop&amp;quot;"
date: 2008-07-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jbeaunaux on 2008-07-10
I'm completely new to Ubuntu, running a Dell Inspiron 530n that had been delivered w/ 7.10 but that I have updated to 8.04.

I've been running into problems trying to install an adobe/flash plug-in for Firefox 3, launching Synaptic Package Manager, launching Software Sources, or running various different commands in the Terminal. In these situations I've been receiving the same error message which tells me 'unable to resolve host dell-desktop'. I've taken a look in my System Log viewer after trying to launch Synaptic to see if I could try to figure out what's going on. This is what I see under /var/log -> auth.log:

Jul 9 21:28:35 dell-desktop sudo: john-daniel: unable to resolve host dell-desktop
Jul 9 21:28:35 dell-desktop sudo: PAM unable to dlopen(lib/security/pam_smbpass.so
Jul 9 21:28:35 dell-desktop sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
Jul 9 21:28:35 dell-desktop sudo: PAM adding faulty module: /lib/security/pam_smbpass.so

I'm guessing that there is some sort of issue launching the script that runs the password security box which comes up when running most of the functions under Administration. Is there any way of correcting this, and how should I go about doing it? Thanks!

---

