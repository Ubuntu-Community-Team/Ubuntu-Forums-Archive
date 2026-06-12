---
title: "Updates"
date: 2009-02-21
forum: General Help
---

### Post by shadowdude1794 on 2009-02-21
Every time I check for new updates in the update manager, this error pops up: 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 978228591BD3A65C
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B00E04A9D58062FB
W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg](http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg)  Unable to connect to wine.budgetdedicated.com http: [IP: 81.171.111.184 80]

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/intrepid/main/i18n/Translation-en_US.bz2)  Unable to connect to wine.budgetdedicated.com http: [IP: 81.171.111.184 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.




Not that big of a deal, it's just annoying. Is there a way to fix this? I'm running 8.10.
Thanks!

---

### Post by Faolan on 2009-02-21
See if this link works:

[Gentoo Blog]("http://gentoo-blog.de/?p=501")

Seems to be a similar problem.

---

### Post by shadowdude1794 on 2009-02-21
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 978228591BD3A65C
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B00E04A9D58062FB


No dice...

---

### Post by binbash on 2009-02-21
save this as change.pl : 

```

#!/usr/bin/env perl
# Perl script to fix Launchpad PPA links and import required keys.
# VERSION: 1.2
#
# Requires: HTML::Parser IO::Socket::SSL
# sudo apt-get install libhtml-parser-perl libio-socket-ssl-perl
#
# Copyright (c) 2009 Savvas Radevic <vicedar@gmail.com>
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#
# UPDATES:
# 1.2:
#    * Added md5sum check for sources.list
#    * Added support for /etc/apt/sources.list.d/*.list
# 1.1:
#    * Added support for key format in edge.launchpad.net server.
#    * Needs IO::Socket::SSL
#
# Do NOT edit unless you know what you're doing!

use strict;
use LWP::Simple qw(get);
use Digest::file qw(digest_file_hex);

my $aptdir = '/etc/apt';
my $sourcelist = $aptdir.'/sources.list';
my $sourceparts = $aptdir.'/sources.list.d';
my $backupext = '.backup';
my $tmpfilename = '/tmp/lp_change.list';
my @lplink = ('http://launchpad.net/~','/+archive/ppa');
my (@allsources, @lpusers);

# Return .list files
@allsources = grep{ -f $_ and /\.list$/ } glob("$sourceparts/*");
# Add main source
if (-f $sourcelist) { push(@allsources, $sourcelist); }
print("Found apt source list files:\n  ".join("\n  ",@allsources)."\n");

foreach my $filename (@allsources) {
    my @new = ();
    print("\nChecking file $filename\n");
    open(S, $filename) or die $!;
    foreach my $l (<S>) {
        if ($l =~ m!^deb(?:-src)?\s+http://ppa.launchpad.net/(\S+)/ubuntu!i) {
            my $r = $1;
            if ($r !~ m!/ppa$!i) {
                $r =~ s!$!/ppa!i;
                $l =~ s!^(deb(?:-src)?\s+http://ppa.launchpad.net/)\S+(/ubuntu)!${1}${r}${2}!i;
                print("Detected/Fixed: $l");
            }
            else {
                print("Detected/Correct: $l");
            }
            $r =~ s!/ppa$!!i;
            # Look if user $r is already on @lpusers - if not, add
            my %lookup = map { $_ => undef } @lpusers;
            if (not exists $lookup{$r}) { push(@lpusers, $r); }
        }
        push(@new, $l);
    }

    close(S);
    open(W, ">$tmpfilename") or die $!;
    print W @new;
    close(W);
    if (digest_file_hex($tmpfilename, "MD5") != digest_file_hex($filename, "MD5")) {
        print("Detected differences between $tmpfilename and $filename\n");
        print("Moving temporary file as $filename\n");
        print("INFO: Enter your administrator password if asked\n\n");
        my @s = ('sudo', 'cp', '-f', $filename, $filename.$backupext);
        system(@s) == 0 or die("system @s failed: $?\n");
        my @s = ('sudo', 'mv', $tmpfilename, $filename);
        system(@s) == 0 or die("system @s failed: $?\n");
    }
    else {
        print("No change for $filename\n");
    }
}

if (defined(@lpusers)) {
    print("Will retrieve keys for: @lpusers\n");
}
else {
    print("\nNo Launchpad PPA links/users detected, exiting.\n");
}

my $getkey = GetKey->new;
foreach my $u (@lpusers) {
    my $url = $lplink[0].$u.$lplink[1];
    print("Attempting to get Launchpad key for $u: $url\n");
    my $html = get($url);
    $getkey->parse($html);
}


package GetKey;
use base qw(HTML::Parser);
use IO::Socket::SSL;
my ($div_tag, $code_tag);
sub start {
    my ($self, $tag, $attr, $attrlist, $origtext) = @_;
    # If HTML tag is "a" (or "A")
    if ($tag =~ /^div$/i and $attr->{id} and $attr->{id} eq 'signing-key') {
        $div_tag = 1;
    }
    elsif ($tag =~ /^code$/i and $div_tag) {
        $code_tag = 1;
    }
}
sub text {
    my ($self, $plaintext) = @_;
    # If we're in the anchor tag, and text is "http" or "ftp"
    if ($div_tag and $code_tag) {
        #New LP uses 1024R/247D1CFF instead of D2BB86E0EBD0F0A43D4DB3A760D11217247D1CFF format
        if ($plaintext =~ m!/([\w\d]+)!i) { $plaintext = $1; }
        print("Found key: $plaintext\n");
        &importkey($plaintext);
    }
}
sub end {
    my ($self, $tag, $origtext) = @_;
    if ($tag =~ /^div$/i) { $div_tag = 0; }
    elsif ($tag =~ /^code$/i) { $code_tag = 0; }
}
sub importkey {
    my ($key) = @_;
    print("Adding $key to your username's gpg\n");
    my @a = ('gpg', '--keyserver', 'keyserver.ubuntu.com', '--recv-keys', $key);
    system(@a) == 0 or print("system @a failed: $?\n");
    
    print("Adding key to apt\n");
    my $b = "gpg --export --armor $key | sudo apt-key add -";
    print("INFO: Enter your administrator password if asked\n\n");
    my $command = `$b`;
    print("$command\n");
}

```

Then make it executable (chmod +x filename) , then run it : 

perl change.pl

---

### Post by shadowdude1794 on 2009-02-21
```

Can't locate IO/Socket/SSL.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at change.pl line 110.
BEGIN failed--compilation aborted at change.pl line 110.

```
Did all of that, that^ happened.

---

### Post by shadowdude1794 on 2009-02-21
*bump*

---

### Post by dorkdork777 on 2009-02-21
The way I sorted out this problem for me, was to find the Launchpad URL of the PPAs that were giving me trouble, for example this:

[https://launchpad.net/~do-core/+archive/ppa](https://launchpad.net/~do-core/+archive/ppa)

[Then follow this screencast]("http://www.youtube.com/watch?v=UUZOQsNo_ws") to add the GPG keys. Good luck :)

EDIT: start the video around 1:18 for what you need.

---

### Post by shadowdude1794 on 2009-02-21
Thanks, I ended up using these commands, insert the numbers/letters where the **************** are. 
```

user@ubuntu:~$ gpg --keyserver keyserver.ubuntu.com --recv ****************
user@ubuntu:~$ gpg --export --armor *************** | sudo apt-key add -

```
Hope this helps!

---

### Post by forger on 2009-02-22
Read this:
[thread=1056099]**Update your Launchpad PPA repositories and apt keys**[/thread]

---

### Post by mb_webguy on 2009-02-22
> **shadowdude1794 said:**
> Thanks, I ended up using these commands, insert the numbers/letters where the **************** are. 
```

user@ubuntu:~$ gpg --keyserver keyserver.ubuntu.com --recv ****************
user@ubuntu:~$ gpg --export --armor *************** | sudo apt-key add -

```
Hope this helps!

This is the simplest and best solution I've seen so far.  The output of "sudo apt-get update" identifies the key(s) you need.  And you can put these two commands in a simple script to make it easier to install the keys.```
#! /bin/sh
gpg --keyserver keyserver.ubuntu.com --recv $1
gpg --export --armor $1 | sudo apt-key add -

```
If you make this script executable (using the command "chmod a+x addkey") and drop it in a bin directory under your user's home directory, you can get the PPA key by simply typing "addkey *keyid*".

---

### Post by rdmike on 2009-02-23
Hi all,

I don't mean to be redundant but, as a linux newbie, this was giving me a hard time too. I tried to use the script mentioned in the forums but without success as I couldn't figure out how to get the script to run. Since the issue started after I attempted to update openoffice I amended my google search to include that term and found this [blog post]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml") which solved the problem for me. 

I only post in the hope it will help someone else; these forums have been awesome to me!

---

### Post by forger on 2009-02-24
Which script rdmike? There are two floating around, I have a perl script here which fixes your PPA links and your GPG keys:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by jackharvest on 2009-10-11
> **mb_webguy said:**
> This is the simplest and best solution I've seen so far.  The output of "sudo apt-get update" identifies the key(s) you need.  And you can put these two commands in a simple script to make it easier to install the keys.```
#! /bin/sh
gpg --keyserver keyserver.ubuntu.com --recv $1
gpg --export --armor $1 | sudo apt-key add -

```If you make this script executable (using the command "chmod a+x addkey") and drop it in a bin directory under your user's home directory, you can get the PPA key by simply typing "addkey *keyid*".

PERFECT. Thanks a million. Keyless repositories are annoying. -__- Thanks again!

---

