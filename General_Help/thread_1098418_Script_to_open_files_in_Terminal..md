---
title: "Script to open files in Terminal."
date: 2009-03-17
forum: General Help
---

### Post by dyingsun on 2009-03-17
Hi, Im not very used to linux scripts, but what I want to do is create a script to leave on my desktop, that drops to terminal, navigates to a particular folder and opens vim. I just don't know how to tell a script to open the terminal window - could anybody clue me in, please? It'd save me a fair bit of time if I only have to click an icon on the desktop!

I've had a google around, but can't find the answer. Can anybody recommend a good scripting tutorial so I don't have to keep pestering you guys?

Thanks!

---

### Post by ruel- on 2009-03-17
I'll make you a simple perl script, but can you give more details? I don't seem to understand what you're trying to do(sorry bout that)..

So you want to place that script on the desktop, double click on that script, opens terminal in a directory, then open vim with which file?

---

### Post by dyingsun on 2009-03-17
rofl, ok, well I was talking more about shellscripts than Perl :)

All i really want to do is batch a few commands together.

Open a term window.

[LIST=1]
[*]nav to /var/www/php
[*]ls -l
[*]vim
[*]leave term window after closing vim.
[/LIST]

(if possible sometime I'd use a prompted variable so vim will open the php file I want.)

I just don't know how to make it open and stay in terminal.

Nice perl script anyway, but what happens if the user != "gay"? heheh!

Thanks!

---

### Post by ruel- on 2009-03-17
its my sig.. its a part of a C++ code not a perl script.. :p

well, I'm not used to shell scripts, I use perl to do these kind of things for me.. :p

anyway hold on.. I'll try to make yo a script.. xD

---

### Post by ruel- on 2009-03-17
```
#!/usr/bin/perl
#tested -ruel
use strict;
use warnings;
chdir('/var/www/php');
system ('ls -l');
print "Enter the file you wish to edit: ";
my $file = <STDIN>;
$file =~ s/^\s+//;
$file =~ s/\s+$//;
my $vim = "vim " . $file;
system($vim);
system('bash');
```

there.. works fine for me.. :p

---

### Post by dyingsun on 2009-03-18
Thanks Ruel, I'll give it a whirl!

---

