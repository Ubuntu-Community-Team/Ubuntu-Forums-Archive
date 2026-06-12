---
title: "Problem installing Net::LDAP perl module"
date: 2009-03-27
forum: General Help
---

### Post by Duree on 2009-03-27
Trying to get a cgi script to run on apache2 and get error that Net::LDAP is not found.  Tried running 'cpan -i Net::LDAP' and it looks good until the end.  Not sure what to do.

Help!

really long output, here's the end of it:
...
Warning (usually harmless): 'YAML' not installed, will not store persistent state

  CPAN.pm: Going to build G/GB/GBARR/Convert-ASN1-0.22.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for Convert::ASN1
Could not read '/home/frodo/.cpan/build/Convert-ASN1-0.22-NY9jnW/META.yml'. Falling back to other methods to determine prerequisites
  GBARR/Convert-ASN1-0.22.tar.gz
  make -- NOT OK
Warning (usually harmless): 'YAML' not installed, will not store persistent state
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running make for G/GB/GBARR/perl-ldap-0.39.tar.gz
  Has already been unwrapped into directory /home/frodo/.cpan/build/perl-ldap-0.39-g4QbOD

  CPAN.pm: Going to build G/GB/GBARR/perl-ldap-0.39.tar.gz

Warning: Prerequisite 'Convert::ASN1 => 0.07' for 'G/GB/GBARR/perl-ldap-0.39.tar.gz' failed when processing 'G/GB/GBARR/Convert-ASN1-0.22.tar.gz' with 'make => NO'. Continuing, but chances to succeed are limited.
  GBARR/perl-ldap-0.39.tar.gz
  make -- NOT OK
Warning (usually harmless): 'YAML' not installed, will not store persistent state
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
$


Then I tried to install 'YAML'

...
YAML-0.68/t/test.t
YAML-0.68/t/TestYAML.pm
CPAN: File::Temp loaded ok (v0.18)
Warning (usually harmless): 'YAML' not installed, will not store persistent state

  CPAN.pm: Going to build I/IN/INGY/YAML-0.68.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for YAML
Could not read '/home/frodo/.cpan/build/YAML-0.68-UY3kds/META.yml'. Falling back to other methods to determine prerequisites
  INGY/YAML-0.68.tar.gz
  make -- NOT OK
Warning (usually harmless): 'YAML' not installed, will not store persistent state
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
:/etc/perl/CPAN$

---

### Post by MrMojoRisin on 2009-05-13
If I'm on Ubuntu, I prefer to install Perl libraries from Ubuntu packages instead of compiling from CPAN.

Try 'sudo apt-get install libnet-ldap-perl'

Kind regards,

Michiel

BTW if you really want to use the CPAN I guess your issue is you don't have a C compiler setup: try 'sudo apt-get install build-essential', then retry cpan.

---

### Post by dasking on 2011-02-03
at -e line 1
make: *** [pure_site_install] Error 13
  ADAMK/YAML-0.72.tar.gz
  /usr/bin/make install  -- NOT OK
Warning (usually harmless): 'YAML' not installed, will not store persistent state


and i installed the library
sudo apt-get install libnet-ldap-perl
[sudo] password for dasking22: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libnet-ldap-perl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 251 not upgraded

---

