---
title: "Apt-cacher importer not working - desperately needed!"
date: 2008-12-13
forum: General Help
---

### Post by hashbrowns on 2008-12-13
I have about 7 intrepid machines here in a lab, and I'd like to be updating them all from my server using apt-cacher. I have one of the machines as my "tester" that i put apt-cacher on (using the instructions [here]("http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher") and [here]("https://help.ubuntu.com/community/Apt-Cacher-Server")) and I have about 400 MB of data from the repositories that I'd like to see if another client can pull.

First, I need to import the data, per the instructions.

But when I try from the terminal, it gives me the following error:

```
/usr/share/apt-cacher/apt-cacher-import.pl: line 32: require: command not found
/usr/share/apt-cacher/apt-cacher-import.pl: line 34: syntax error near unexpected token `('
/usr/share/apt-cacher/apt-cacher-import.pl: line 34: `use Getopt::Long qw(:config no_ignore_case bundling pass_through);'

```

Does anyone have any idea what could be causing this? Both my test "server" and my client are running brand new installs of intrepid. I've already tried connecting the client to the apt-cacher system, and it seems to find it and try to update itself, but of course it cannot because there aren't any .debs in there yet.

---

### Post by tigerstripedcat on 2008-12-13
A couple of possibilites:

1) Badly codded perl
2) You are running on an old version of perl
3) You need a require shell command, which I couldn't find

Make sure you are installing all the dependencies.  Do you have Getopt:Long installed?

Maybe it's one of these:
jmorris@faye:~$ sudo apt-cache search getopt -i | grep perl -i
libgetopt-argvfile-perl - Perl module for reading script options and parameters from files
libgetopt-declare-perl - Getopt::Declare command line argument parser
libgetopt-euclid-perl - Executable Uniform Command-Line Interface Descriptions
libgetopt-mixed-perl - Perl module for processing options in GNU-style (= long and short)
libgetopt-tabular-perl - table-driven argument parsing for Perl 5
libmoosex-getopt-perl - A Moose role for processing command line options


TSC

---

### Post by dwanders on 2008-12-16
Silly question - but did you run it as su or with sudo? I just install apt-cacher on my home PC's and it seems to be working out very well. I seem to recall I had to run it twice to import the files from my host PC, and it was something like: 

sudo /usr/share/apt-cacher/apt-cacher-import.pl /var/cache/apt/archives/

(I think I added that last slash or something)

I began by following the first link you had and got pretty confused - when I came across the second link and got it all working very well. Still a bit fuzzy for me - but seems to be working.

---

