---
title: "bash script help"
date: 2009-04-10
forum: General Help
---

### Post by prem1er on 2009-04-10
I know this isn't an Ubuntu specific issue, but I usually get good suggestions when I post this sort of stuff here.  I am trying to write a bash script for my mp3's.  I have 2 drives on my server at home, one which I download/seed music to/from and the other drive which I use to store an organized copy of those same files for streaming and indexing. Each time I download a new album (legally of course) I have to manually copy the file between the 2 drives.  I want to write a bash script that reads the id3's of the mp3's and places them in the correct directory and with the proper formatting.  I'm a little confused as to where to start.  Can anyone point me in the right direction for reading and id3 tag from an mp3 using bash?  Thanks in advance.

---

### Post by prem1er on 2009-04-10
> **prem1er said:**
> I know this isn't an Ubuntu specific issue, but I usually get good suggestions when I post this sort of stuff here.  I am trying to write a bash script for my mp3's.  I have 2 drives on my server at home, one which I download/seed music to/from and the other drive which I use to store an organized copy of those same files for streaming and indexing. Each time I download a new album (legally of course) I have to manually copy the file between the 2 drives.  I want to write a bash script that reads the id3's of the mp3's and places them in the correct directory and with the proper formatting.  I'm a little confused as to where to start.  Can anyone point me in the right direction for reading and id3 tag from an mp3 using bash?  Thanks in advance.

Or could this be done with perl or python?

---

### Post by ghostdog74 on 2009-04-11
you can download ID3 tools that you can use with your shell script, or you can use Perl (or Python). here's an example with Perl's MP3::Tag module. (similar ID3 modules can be found for Python too). first you need to download from CPAN
```

shell> perl -MCPAN -e shell
cpan> install MP3::Tag

```
then write the Perl script
```

#!/usr/bin/perl
use strict;
use warnings;
# use module
use MP3::Tag;
# set filename of MP3 track
my $filename = "test.mp3";
# create new MP3-Tag object
my $mp3 = MP3::Tag->new($filename);
# get tag information
my ($title, $track, $artist, $album, $comment, $year, $genre) = $mp3->autoinfo();
print "$title, $track, $artist, $album, $comment, $year, $genre\n";
....
# code to make directory according to your preferred structure here..
# code to put files to respective directories.

# clean up
$mp3->close();

```

---

### Post by StOoZ on 2009-04-11
for reading mp3 tags info , use mp3info command line utility

> DESCRIPTION
       mp3info  is  a utility used to read and modify the ID3 tags in MPEG layer 3 (MP3) files.  It can also (optionally)
       display various technical attributes of the MP3 file.

---

### Post by prem1er on 2009-04-12
Thanks everyone. I'm looking into the suggestions now, I will post a response and let you know how it worked.

---

