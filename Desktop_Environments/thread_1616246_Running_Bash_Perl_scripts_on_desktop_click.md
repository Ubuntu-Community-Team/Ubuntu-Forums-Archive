---
title: "Running Bash Perl scripts on desktop click"
date: 2010-11-08
forum: Desktop Environments
---

### Post by joe5000 on 2010-11-08
I wanted to run bash and perl scripts which requires SU privileges by clicking on dektop
Terminal window opens and closes fast without knowing what happened.

scripts work on terminal window by telling 
sudo perl   file.pl
sudo bash file.sh

Perl has this header
#!/usr/bin/env perl
or
#!usr/bin/perl -w

Bash has header
#!/bin/bash

How can I run them with desktop shortcuts with SU privilege
so, the terminal will not close after execution?

should not the scripts work without telling perl or bash,
since they have the header?

---

### Post by gmargo on 2010-11-08
Perhaps you can use **gksudo**, a graphical front end for **sudo**.

---

