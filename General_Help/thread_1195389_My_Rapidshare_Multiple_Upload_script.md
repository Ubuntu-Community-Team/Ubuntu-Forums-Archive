---
title: "My Rapidshare Multiple Upload script"
date: 2009-06-23
forum: General Help
---

### Post by darthrax on 2009-06-23
Hello,

I was searching around for a way to upload multiple files to my rapidshare account and i came across the linux perl script that they have written (which you can get here [http://images.rapidshare.com/software/rsapi.pl]("http://images.rapidshare.com/software/rsapi.pl"))

I wanted to automate the process somewhat so i wrote a little script to search for and upload rar files from a directory.

heres the script:

[SIZE="3"]EDIT: PLEASE USE THE SCRIPT FROM POST #11 AND INSTRUCTIONS IN POST #9 AS THAT IS THE LATEST VERSION...[/SIZE]

```

#!/bin/bash
read -p "Enter file string to search and upload: " files
find /location/of/files/ -iname "*$files*.rar" -exec perl rsapi.pl {} prem rapidshareusername rapidsharepassword \;
find /location/of/files/ -iname "*$files*.rar" -exec rm -v {} \;

```

[SIZE="4"]PLEASE NOTE THAT THE ABOVE SCRIPT DELETES THE FILES IT HAS UPLOADED!!! DO NOT RUN ON YOUR IMPORTANT DATA.[/SIZE]

i normally create a temporary .rar to upload to so i like to have the script remove the file after its done. If you don't want to remove the files after upload remove the second find line from the script. 

heres the rapidshare uploader (i copied it from their website i have made no changes)
```

#!/usr/bin/perl

# RapidShare AG OpenSource Perl Uploader V1.0. For non-commercial use only. All rights reserved.
# Included: Uploading to free, collector's and premium-zone. The MD5-check after uploads checks if the upload worked.
# NOT included in this version: Upload-resume via new RS API.
# This is a PERL script written for experts and for coders wanting to know how to write own upload programs.
# Tested under Linux and Linux only.
# If you write your own upload-tools, please look at our rsapi.cgi calls. You need them to have fun.
#
# To upload a file, put this script on a machine with perl installed and use the following syntax:
# perl rsapi.pl mytestfile.rar             (this uploads mytestfile.rar as a free user)
# perl rsapi.pl archive.rar prem 334 test  (this uploads archive.rar to the premium-zone of login 334 with password test)
# perl rsapi.pl a.rar col testuser mypw    (this uploads a.rar to the collector's-zone of login testuser with password mypw)
#
# We will publish another version with upload resume enabled soon, but this script actually works and we actually
# want you to understand how it works and upload resume would make this script even more complex.

use strict;
use warnings;
use Digest::MD5("md5_hex");
use Fcntl;
use IO::Socket;

my ($file, $filename, $uploadpath, $size, $socket, $uploadserver, $cursize, $fh, $bufferlen, $buffer, $boundary, $header, $contentheader,
$contenttail, $contentlength, $result, $maxbufsize, $md5hex, $filecontent, $size2, %key_val, $login, $password, $zone);



# This chapter sets some vars and parses some vars.
$/ = undef;
$file = $ARGV[0] || die "Syntax: $0 <filename to upload> <free|prem|col> [login] [password]\n";
$zone = $ARGV[1] || "";
$login = $ARGV[2] || "";
$password = $ARGV[3] || "";
$maxbufsize = 64000;
$uploadpath = "l3";
$cursize = 0;
$size = -s $file || die "File $file is empty or does not exist!\n";
$filename = $file =~ /[\/\\]([^\/\\]+)$/ ? $1 : $file;



# This chapter checks the file and calculates the MD5HEX of the existing local file.
print "File $file has $size bytes. Calculating MD5HEX...\n";
open(FH, $file) || die "Unable to open file: $!\n";
$filecontent = <FH>;
close(FH);
$md5hex = uc(md5_hex($filecontent));
$size2 = length($filecontent);
print "MD5HEX is $md5hex ($size2 bytes analyzed.)\n";
unless ($size == $size2) { die "Strange error: $size bytes found, but only $size2 bytes analyzed?\n" }



# This chapter finds out which upload server is free for uploading our file by fetching http://rapidshare.com/cgi-bin/rsapi.cgi?sub=nextuploadserver_v1
if ($login and $password) { print "Trying to upload to your premium account.\n" } else { print "Uploading as a free user.\n" }
print "Uploading as filename '$filename'. Getting upload server infos.\n";
$socket = IO::Socket::INET->new(PeerAddr => "rapidshare.com:80") || die "Unable to open port: $!\n";
print $socket qq|GET /cgi-bin/rsapi.cgi?sub=nextuploadserver_v1 HTTP/1.0\r\n\r\n|;
($uploadserver) = <$socket> =~ /\r\n\r\n(\d+)/;
unless ($uploadserver) { die "Uploadserver invalid? Internal error!\n" }
print "Uploading to rs$uploadserver$uploadpath.rapidshare.com\n";



# This chapter opens our file and the TCP socket to the upload server.
sysopen($fh, $file, O_RDONLY) || die "Unable to open file: $!\n";
$socket = IO::Socket::INET->new(PeerAddr => "rs$uploadserver$uploadpath.rapidshare.com:80") || die "Unable to open port: $!\n";



# This chapter constructs a (somewhat RFC valid) HTTP header. See how we pass rsapi_v1=1 to the server to get a program-friendly output.
$boundary = "---------------------632865735RS4EVER5675865";
$contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="rsapi_v1"\r\n\r\n1\r\n|;

if ($zone eq "prem" and $login and $password) {
  $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="login"\r\n\r\n$login\r\n|;
  $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="password"\r\n\r\n$password\r\n|;
}

if ($zone eq "col" and $login and $password) {
  $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="freeaccountid"\r\n\r\n$login\r\n|;
  $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="password"\r\n\r\n$password\r\n|;
}

$contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="filecontent"; filename="$filename"\r\n\r\n|;
$contenttail = "\r\n$boundary--\r\n";
$contentlength = length($contentheader) + $size + length($contenttail);
$header = qq|POST /cgi-bin/upload.cgi HTTP/1.0\r\nContent-Type: multipart/form-data; boundary=$boundary\r\nContent-Length: $contentlength\r\n\r\n|;



#This chapter actually sends all the data, header first, to the upload server.
print $socket "$header$contentheader";

while ($cursize < $size) {
  $bufferlen = sysread($fh, $buffer, $maxbufsize, 0) || 0;
  unless ($bufferlen) { die "Error while sending data: $!\n" }
  print "$cursize of $size bytes sent.\n";
  $cursize += $bufferlen;
  print $socket $buffer;
}

print $socket $contenttail;



# OK, all is sent. Now lets fetch the server's reponse and analyze it.
print "All $size bytes sent to server. Fetching result:\n";
($result) = <$socket> =~ /\r\n\r\n(.+)/s;
unless ($result) { die "Ooops! Did not receive any valid server results?\n" }
print "$result >>> Verifying MD5...\n";

foreach (split(/\n/, $result)) {
  if ($_ =~ /([^=]+)=(.+)/) { $key_val{$1} = $2 }
}



# Now lets check if the result contains (and it should contain) the MD5HEX of the uploaded file and check if its identical to our MD5HEX.
unless ($key_val{"File1.4"}) { die "Ooops! Result did not contain MD5? Maybe you entered invalid login data.\n" }
if ($md5hex ne $key_val{"File1.4"}) { die qq|Upload FAILED! Your MD5HEX is $md5hex, while the uploaded file has MD5HEX $key_val{"File1.4"}!\n| }
print "MD5HEX value correct. Upload completed without errors. Saving links to rsulres.txt\n\n\n";



# Maybe you want the links saved to a logfile? Here we go.
open(O, ">>rsulres.txt");
print O $result . "\n";
close(O);



# Thats it. Have fun experimenting with this script. Now lets say...
exit;

```

Usage:
You basically copy the two code fragments into separate files. The first bash script can be named anything (i named mine rsup.sh) but the second one needs to be named "rsapi.pl".

Make sure to change the permissions of the files so that they can both be executed as programs. From the file manager right click on the files individually and click on properties. Goto the permissions tab and make sure that the Allow executing file as program is ticked.

After that start a terminal and cd into the directory you saved rsup.sh in, and run the script with:

```
./rsup.sh
```

My output for a 'test' search string:

```
anthrax@anand:~/rsup$ ./rsup.sh
Enter file string to search and upload: test
File /home/anthrax/rsup/files/test1.rar has 2492 bytes. Calculating MD5HEX...
MD5HEX is E5B58CEAE166C332D4350AFCFECD3AF5 (2492 bytes analyzed.)
Trying to upload to your premium account.
Uploading as filename 'test1.rar'. Getting upload server infos.
Uploading to rs231l3.rapidshare.com
0 of 2492 bytes sent.
All 2492 bytes sent to server. Fetching result:
savedfiles=1 forbiddenfiles=0 premiumaccount=******* freeowner=0
File1.1=http://rapidshare.com/files/247892799/test1.rar.html
File1.2=
File1.3=
File1.4=
File1.5=Completed
 >>> Verifying MD5...
MD5HEX value correct. Upload completed without errors. Saving links to rsulres.txt


File /home/anthrax/rsup/files/test.rar has 2492 bytes. Calculating MD5HEX...
MD5HEX is E5B58CEAE166C332D4350AFCFECD3AF5 (2492 bytes analyzed.)
Trying to upload to your premium account.
Uploading as filename 'test.rar'. Getting upload server infos.
Uploading to rs622l3.rapidshare.com
0 of 2492 bytes sent.
All 2492 bytes sent to server. Fetching result:
savedfiles=1 forbiddenfiles=0 premiumaccount=******* freeowner=0
File1.1=http://rapidshare.com/files/247892810/test.rar.html
File1.2=
File1.3=
File1.4=
File1.5=Completed
 >>> Verifying MD5...
MD5HEX value correct. Upload completed without errors. Saving links to rsulres.txt


File /home/anthrax/rsup/files/test2.rar has 2492 bytes. Calculating MD5HEX...
MD5HEX is E5B58CEAE166C332D4350AFCFECD3AF5 (2492 bytes analyzed.)
Trying to upload to your premium account.
Uploading as filename 'test2.rar'. Getting upload server infos.
Uploading to rs744l3.rapidshare.com
0 of 2492 bytes sent.
All 2492 bytes sent to server. Fetching result:
savedfiles=1 forbiddenfiles=0 premiumaccount=******* freeowner=0
File1.1=http://rapidshare.com/files/247892826/test2.rar.html
File1.2=
File1.3=
File1.4=
File1.5=Completed
 >>> Verifying MD5...
MD5HEX value correct. Upload completed without errors. Saving links to rsulres.txt


removed `/home/anthrax/rsup/files/test1.rar'
removed `/home/anthrax/rsup/files/test.rar'
removed `/home/anthrax/rsup/files/test2.rar'
```

There is a lot that can be done with this script. At the moment it's only asking for the filename to search for in a specific directory (assuming you keep all your upload files in the same directory like i do), and it is only searching for .rar files(i mainly upload .rar's) . If you want to specify the directory with the files in it as part of the input use this script instead:

```
#!/bin/bash
read -p "Enter the location to search for files: " location
read -p "Enter file string to search and upload: " files
find $location -iname "*$files*.rar" -exec perl rsapi.pl {} prem rapidshareusername rapidsharepassword \;
find $location -iname "*$files*.rar" -exec rm -v {} \;
```

You can of course modify the filetypes and any of the other search parameters.

I hope that this helps some people. If it does post a reply. Also if anyone has any suggestions on how to improve the script please let me know.

Now we need somebody to give this a GUI.:D

---

### Post by novize on 2009-07-20
Thanks, it works great! :)

Is there a way to resume uploads? 

PS: Sorry for my english. I am a Greek who lives now in Greece, but who lived 27 years in Germany. So I had to learn greek and german... and I can not speek english very well.

---

### Post by darthrax on 2009-07-27
heres the new rapidshare upload script v2.1.1

i believe that the syntax has changed from:
```
# perl rsapi.pl mytestfile.rar             (this uploads mytestfile.rar as a free user)
# perl rsapi.pl archive.rar prem 334 test  (this uploads archive.rar to the premium-zone of login 334 with password test)
# perl rsapi.pl a.rar col testuser mypw    (this uploads a.rar to the collector's-zone of login testuser with password mypw)

```

to
```
# perl rsapi.pl free mytestfile.rar        (this uploads mytestfile.rar as a free user)
# perl rsapi.pl prem archive.rar 334 test  (this uploads archive.rar to the premium-zone of login 334 with password test)
# perl rsapi.pl col a.rar testuser mypw    (this uploads a.rar to the collector's-zone of login testuser with password mypw)
```

so change the script accordingly.

```
#!/usr/bin/perl

# Version 2.1.1 (13. July 2007)

# RapidShare AG OpenSource Perl Uploader V2 (with upload resume). For non-commercial use only. All rights reserved.
# Included: Uploading to free, collector's and premium-zone. The MD5-check after uploads checks if the upload worked.
# Upload resume can continue aborted downloads up to 24 hours after the download aborted. This means, incomplete files
# will automatically be deleted from the RapidShare servers 24 hours after the first chunk arrived.
# This is a PERL script written for experts and for coders wanting to know how to write own upload programs.
# Tested under Linux and Linux only.
# If you write your own upload-tools, please look at our rsapi.cgi calls. You need them to have fun.
#
# To upload a file, put this script on a machine with perl installed and use the following syntax:
# perl rsapi.pl free mytestfile.rar        (this uploads mytestfile.rar as a free user)
# perl rsapi.pl prem archive.rar 334 test  (this uploads archive.rar to the premium-zone of login 334 with password test)
# perl rsapi.pl col a.rar testuser mypw    (this uploads a.rar to the collector's-zone of login testuser with password mypw)

use strict;
use warnings;
use Digest::MD5("md5_hex");
use Fcntl;
use IO::Socket;

my ($file, $zone, $login, $password, $uploadpath, $cursize, $size, $filecontent, $md5hex, $size2, $socket, $uploadserver, $killcode);



# This chapter sets some vars and parses some vars.
$/ = undef;
$SIG{PIPE} = 'IGNORE';
$file = $ARGV[0] || die "Syntax: $0 <filename to upload> <free|prem|col> [login] [password]\n";
$zone = $ARGV[1] || "";
$login = $ARGV[2] || "";
$password = $ARGV[3] || "";
$uploadpath = "l3";
$size = -s $file || die "File $file is empty or does not exist!\n";



# This chapter checks the file and calculates the MD5HEX of the existing local file.
print "File $file has $size bytes. Calculating MD5HEX...\n";
open(FH, $file) || die "Unable to open file: $!\n";
$filecontent = <FH>;
close(FH);
$md5hex = md5_hex($filecontent);
$size2 = length($filecontent);
print "MD5HEX is $md5hex ($size2 bytes analyzed)\n";
unless ($size == $size2) { die "Strange error: $size bytes found, but only $size2 bytes analyzed?\n" }



# This chapter finds out which upload server is free for uploading our file by fetching http://rapidshare.com/cgi-bin/rsapi.cgi?sub=nextuploadserver_v1
if ($login and $password) { print "Trying to upload to your $zone account.\n" } else { print "Uploading as a free user.\n" }
print "Getting upload server infos.\n";
$socket = IO::Socket::INET->new(PeerAddr => "rapidshare.com:80") || die "Unable to open port: $!\n";
print $socket qq|GET /cgi-bin/rsapi.cgi?sub=nextuploadserver_v1 HTTP/1.0\r\n\r\n|;
($uploadserver) = <$socket> =~ /\r\n\r\n(\d+)/;
unless ($uploadserver) { die "Uploadserver invalid? Internal error!\n" }
print "Uploading to rs$uploadserver$uploadpath.rapidshare.com\n";

$cursize = 0;
while ($cursize < $size) { $cursize = &uploadchunk($file, $md5hex, $size, $cursize, "rs$uploadserver$uploadpath.rapidshare.com:80") }



sub uploadchunk {
  my $file = shift || die;
  my $md5hex = shift || die;
  my $size = shift || die;
  my $cursize = shift || 0;
  my $fulluploadserver = shift || die;

  my ($uploaddata, $wantchunksize, $fh, $socket, $boundary, $contentheader, $contenttail, $contentlength, $header, $chunks, $chunksize,
$bufferlen, $buffer, $result, $fileid, $complete, $resumed, $filename);

  if (-e "$file.uploaddata") {
    print "Found .uploaddata! Overriding settings and trying to resume.\n";
    open(I, "$file.uploaddata") or die "Unable to open file: $!\n";
    ($fulluploadserver, $fileid, $killcode) = split(/\n/, <I>);
    print "Uploadserver=$fulluploadserver\nFile-ID=$fileid\nKillcode=$killcode\n";
    close(I);
    print "Checking if RS gives an OK and the position...\n";
    $socket = IO::Socket::INET->new(PeerAddr => "rapidshare.com:80") || die "Unable to open port: $!\n";
    print $socket qq|GET /cgi-bin/rsapi.cgi?sub=checkincomplete_v1&fileid=$fileid&killcode=$killcode HTTP/1.0\r\n\r\n|;
    $result = <$socket>;
    unless ($result =~ /\r\n\r\n(\d+)/) { die "I can't resume the file. Please delete $file.uploaddata. RS said:\n$result\n" }
    $cursize = $1;
    print "All ok. The upload stopped at $cursize. Trying to resume.\n";
    $resumed = 1;
  }

  $wantchunksize = 1024000;

  if ($size > $wantchunksize) {
    $chunks = 1;
    $chunksize = $size - $cursize;
    if ($chunksize > $wantchunksize) { $chunksize = $wantchunksize } else { $complete = 1 }
  } else {
    $chunks = 0;
    $chunksize = $size;
  }

  print "Upload chunk is $chunksize bytes starting at $cursize.\n";

  sysopen($fh, $file, O_RDONLY) || die "Unable to open file: $!\n";
  $filename = $file =~ /[\/\\]([^\/\\]+)$/ ? $1 : $file;
  $socket = IO::Socket::INET->new(PeerAddr => $fulluploadserver) || die "Unable to open socket: $!\n";
  $boundary = "---------------------632865735RS4EVER5675865";
  $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="rsapi_v1"\r\n\r\n1\r\n|;

  if ($resumed) {
    $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="fileid"\r\n\r\n$fileid\r\n|;
    $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="killcode"\r\n\r\n$killcode\r\n|;
    if ($complete) { $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="complete"\r\n\r\n1\r\n| }
  } else {
    if ($zone eq "prem" and $login and $password) {
      $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="login"\r\n\r\n$login\r\n|;
      $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="password"\r\n\r\n$password\r\n|;
    }

    if ($zone eq "col" and $login and $password) {
      $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="freeaccountid"\r\n\r\n$login\r\n|;
      $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="password"\r\n\r\n$password\r\n|;
    }

    if ($chunks) { $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="incomplete"\r\n\r\n1\r\n| }
  }

  $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="filecontent"; filename="$filename"\r\n\r\n|;
  $contenttail = "\r\n$boundary--\r\n";
  $contentlength = length($contentheader) + $chunksize + length($contenttail);

  if ($resumed) {
    $header = qq|POST /cgi-bin/uploadresume.cgi HTTP/1.0\r\nContent-Type: multipart/form-data; boundary=$boundary\r\nContent-Length: $contentlength\r\n\r\n|;
  } else {
    $header = qq|POST /cgi-bin/upload.cgi HTTP/1.0\r\nContent-Type: multipart/form-data; boundary=$boundary\r\nContent-Length: $contentlength\r\n\r\n|;
  }

  print $socket "$header$contentheader";

  sysseek($fh, $cursize, 0);
  $bufferlen = sysread($fh, $buffer, $wantchunksize) || 0;
  unless ($bufferlen) { die "Error while reading file: $!\n" }
  print "Sending $bufferlen bytes.\n";
  $cursize += $bufferlen;
  print $socket $buffer;
  print $socket $contenttail;
  print "Server response:\n";
  ($result) = <$socket> =~ /\r\n\r\n(.+)/s;
  unless ($result) { die "Ooops! Did not receive any valid server results?\n" }
  print $result . "\n";

  if ($resumed) {
    if ($complete) {
      if ($result =~ /^COMPLETE,(\w+)/) {
        print "Upload completed! MD5HEX=$1 Checking MD5...\n";
        if ($md5hex ne $1) { die "MD5-CHECK NOT PASSED! LOCAL=$md5hex REMOTE=$1\n" }
        print "MD5-check passed. Upload OK! Saving status to rsapiuploads.txt\n";
        open(O,">>rsapiuploads.txt") or die "Unable to save to rsapiuploads.txt: $!\n";
        print O "Upload OK!\n\n";
        close(O);
        unlink("$file.uploaddata");
      } else {
        die "Unexpected server response!\n";
      }
    } else {
      if ($result =~ /^CHUNK,(\d+)/) {
        print "Chunk upload completed! Uploaded=$1\n";
      } else {
        die "Unexpected server response!\n";
      }
    }
  } else {
    if ($result =~ /files\/(\d+)/) { $fileid = $1 } else { die "Server result did not contain a file ID.\n" }
    unless ($result =~ /File1\.3=(\d+)/ and $1 == $cursize) { die "Server did not save all data we sent.\n" }
    unless ($result =~ /File1\.2=.+?killcode=(\d+)/) { die "Server did not send our killcode.\n" }

    $killcode = $1;

    open(O,">>rsapiuploads.txt") or die "Unable to save to rsapiuploads.txt: $!\n";
    print O "Uploading $file. Download-links:\n$result";
    close(O);

    if ($chunks) {
      open(O, ">$file.uploaddata") or die "Unable to save upload server: $!\n";
      print O "$fulluploadserver\n$fileid\n$killcode\n";
      close(O);
    }
  }

  return $cursize;
}

```

In other news i'm working on a nautilus script that will automate this entire process. Now you can upload to rapidshare by right clicking the target file and selecting rsup! All temporary archives (for filesize greater than 100Mb) are created automatically, uploaded and deleted, essentially making no changes to your system and leaving a backup on rapidshare. Currently testing it. Will post the full thing when it's ready.

---

### Post by GabboCZ on 2009-07-28
Ths a lot man, I was looking some way how to upload files from my home server. 
But I used new RSAPI v2.1.1 and it has still the same syntax as the old one, they had probably eroor in that comment.

---

### Post by moster on 2009-07-28
Thanks for this usefull script. :) Say what happens if connection drop. This is important one.

---

### Post by novize on 2009-08-14
It works super! Thank you very much my friend!!! :)

---

### Post by darthrax on 2009-08-17
> 
Re: My Rapidshare Multiple Upload script
Ths a lot man, I was looking some way how to upload files from my home server.
But I used new RSAPI v2.1.1 and it has still the same syntax as the old one, they had probably eroor in that comment.


Thanks for pointing that out GabboCZ. Your right!! there is an error in the comment because when you run the rsapi.pl in the terminal its output is

```

Syntax: ~/.rsapi.pl <filename to upload> <free|prem|col> [login] [password]

```

---

### Post by binbash on 2009-08-17
I am gonna try it out, thanks.

---

### Post by darthrax on 2009-08-17
Greetings all...

It's finally here...the right-click rapidshare upload!!!:D

there are still a few bugs in it (i feel) but its working and you can use it.

The Procedure:

1. The script requires 7zip so if you don't have it installed type the following code in the terminal 
```

sudo apt-get install p7zip p7zip-full p7zip-rar 
```

2. copy the rapidshare script from above (v2.1.1) and save it in your ~/.gnome2/nautilus-scripts folder as ".rsapi.pl" (note the '.' before the name makes the file hidden so it doesn't show up on your right click menu. also remove the quotes before saving.)

3. copy the following code and save it in your ~/.gnome2/nautilus-scripts folder as "RapidUpload" (or anything else. Remember to remove the quotes). Enter your Rapidshare user name, password and account type in the appropriate place. DO NOT PUT A SPACE (" ") BETWEEN THE = AND YOUR USERNAME/PASSWORD/ACCOUNT TYPE.

```

#!/bin/bash
#
# Right-click upload files to your rapidshare account
#
# Owner: 
#   Anand Kapre
#   ak@anandkapre.com
#
# Licence: GNU GPL
# Copyright (C) Anand Kapre
#
# Dependency:
#   7zip
#
# Created on Tuesday August 18th 2009
#
# Tested on Ubuntu 9.04 Jaunty Jackalope
# accounttype can be free prem col
#
rapidshareusername=username 
rapidsharepassword=password
accounttype=prem
(
files=`echo "$1" | sed 's/ /\\ /g'`
size=$(stat -c%s "$files")
folder=$(pwd)
if [ $size -gt 104857600 ]; then
echo "Filesize greater than 100Mb, adding files to archive..."
7z a -tzip -v99m "$files".zip "$folder"/"$files"
echo "Created temporary archive, Proceeding with upload..."
find "$folder" -iname "*$files*.zip*" -exec ~/.gnome2/nautilus-scripts/.rsapi.pl {} $accounttype $rapidshareusername $rapidsharepassword \;
echo "Upload Completed, DeletiIncompleteng archives..."
find "$folder" -iname "*$files*.zip*" -exec rm -v {} \;
echo "JOB DONE"
else
echo "Filesize lesser than 100Mb, Proceeding with upload..."
find "$folder" -iname "$files" -exec ~/.gnome2/nautilus-scripts/.rsapi.pl {} $accounttype $rapidshareusername $rapidsharepassword \;
echo "JOB DONE"
fi
echo "You may close this window"
) | zenity --title=RapidUpload --text-info --width=500 --height=500

```

4. Make sure both files ".rsapi.pl" and "RapidUpload" are executable. I've described the process in my first post.

5. Thats it!!! Your done.

Usage:

Right click on any file, and goto Scripts > RapidUpload

A dialog will pop up showing you what the program is doing. For files larger than 100Mb the script uses 7zip to compress the files into 100Mb archives. It then uploads the archive(s) and deletes them. So make sure you have at least the same amount of diskspace free for larger files.

The newer version uf rsapi (2.1.1) resumes uploads so broken uploads will be resumed within 24 hours. Broken uploads show up in the Rapidshare Premium / Collecter Zone with an Incomplete Status.

[SIZE="5"]BUGS:

1. Multiple selected files do not work as yet. If you select more than one file to upload at a time the first file will be uploaded that many times.[/SIZE]

2. Two files are created after the script runs one is rsapiuploads.txt and the other is filename.uploaddata. I don't want them but some people may find them useful. I tried to automatically delete them from the script but it's not happening. IF YOUR UPLOAD IS NOT COMPLETE, DO NOT DELETE THESE FILES AS THEY ALLOW YOU TO RESUME THE UPLOAD. EDIT: The filename.uploaddata file is removed automatically by the rsapi.pl script.

3. Cheesy looking text display...I STILL WANT A GUI...SOMEONE HELP ME!!!

If you find any more bugs please let me know... i don't think there are any but you never know. I had some issues with spaces in the path names but i resolved that and the script handles spaces fine now. 

PS: TO RESUME UPLOADS JUST RIGHT CLICK AND RUN RAPIDUPLOAD ON THE SAME FILE AGAIN. ITS THAT SIMPLE :D
you can download the two scripts from 
```

http://rapidshare.com/files/268537486/.rsapi.pl.html
http://rapidshare.com/files/269110306/Rapid_Upload.html

```UPLOADED BY RAPIDUPLOAD!!!

---

### Post by binbash on 2009-08-18
Please fix Bug #1 and i will blog about it. It is not very useful FOR ME with that bug

---

### Post by darthrax on 2009-08-19
Greetings all...

i'm pleased to announce that the script is for all intents and purposes complete... Bug #1 is solved!!! You can now select multiple files, Right click, Select RapidUpload and voila after some time, your files will be backed up on rapidshare. I switched from 7zip to rar as i use flashgot and downthemall in firefox and its easier to automatically start *.rar files than it is to start *.001 *.002 *.003 *.004 *.005 *.006... etc.

in case you don't have rar install it with:
```
sudo apt-get install rar
```

So follow the instructions in post #9 from step 2. and replace the RapidUpload Script there with this one:
```

#!/bin/bash
# Right-click upload files to your rapidshare account
# Owner: 
#   Anand Kapre
#   ak@anandkapre.com
# Licence: GNU GPL
# Copyright (C) Anand Kapre
# Dependency:
#   rar
# Created on Tuesday August 18th 2009
# Tested on Ubuntu 9.04 Jaunty Jackalope
rapidshareusername=username 
rapidsharepassword=password
accounttype=prem
(
folder=$(pwd)
for arg in "$@"
do
if [ ${arg: -4} != ".rar" ]; then
echo "Adding $arg to archive..."
rar a -ep -v99M "$arg".rar "$folder"/"$arg"
echo "Created temporary archive, Proceeding with upload..."
find "$folder" -iname "*$arg*.rar*" -exec ~/.gnome2/nautilus-scripts/.rsapi.pl {} $accounttype $rapidshareusername $rapidsharepassword \;
echo "Upload Completed, Deleting archives..."
find "$folder" -iname "*$arg*.rar*" -exec rm -v {} \;
else
echo "$arg is already a rar archive..."
echo "Uploading $arg..."
find "$folder" -iname "$arg" -exec ~/.gnome2/nautilus-scripts/.rsapi.pl {} $accounttype $rapidshareusername $rapidsharepassword \;
echo "Upload Completed"
fi
done
echo "JOB DONE"
echo "You may close this window"
) | zenity --title=RapidUpload --text-info --width=500 --height=500

```

---

### Post by binbash on 2009-08-23
I blogged it as i promised via P.M with step by step tutorial:

[http://www.ubuntu-inside.me/2009/08/one-click-multi-rapidshare-uploader.html](http://www.ubuntu-inside.me/2009/08/one-click-multi-rapidshare-uploader.html)

---

### Post by novize on 2009-09-08
[darthrax]("http://ubuntuforums.org/member.php?u=666903"), I don' t know how to thank you! With your solution who needs a gui? Thank you very much! You are the best!!!

---

### Post by darthrax on 2009-10-03
Greetings all...

2007 hits... not bad for my first bit of useful software :D....

theres a new rsapi thats been released that gives added functionality like checking the md5sum of your upload against files already in your account to prevent duplicates, adding a trash facility etc. reworking the script to add these features...

also i've created a small little project on sourceforge called [RapidUpload]("https://sourceforge.net/projects/rapidupload/") so all future releases will be posted there... thanks for all the positive feedback...i hope to someday turn this into something with a snazzy gui et al. lets see how it goes...

[https://sourceforge.net/projects/rapidupload/]("https://sourceforge.net/projects/rapidupload/")

---

### Post by joselol on 2009-11-10
Modified script! more gui-ish;)

```
#!/bin/bash
# Right-click upload files to your rapidshare account
# Owner: 
#   José Lourenço
#   joselol1987@gmail.com
# Based on RapidUpload by Anand Kapre - ak@anandkapre.com
# Licence: GNU GPL
# Dependency:
#   rar zenity nautilus gnome2 rsapiresume.pl
# Created on Tuesday November 10th 2009
# Tested on Ubuntu
TYPE=$(zenity --list --text="account:" --radiolist --column="Pick" --column="Opinion" --column="Description" FALSE free "free zone" FALSE prem "premium zone" TRUE col "collector's zone" --width=500 --height=200)
LOGIN=$(zenity --entry --text="username:" --entry-text="username" --width=500)
PASSWORD=$(zenity --entry --text="password:" --entry-text="password" --hide-text --width=500)
UPDATEMODE=$(zenity --list --text="updatemode:" --radiolist --column="Pick" --column="Opinion" --column="Description" FALSE "0" "Traditional uploading, no duplicate checking" TRUE "1" "The lowest file ID duplicate will be overwritten if MD5 differs>" --width=500 --height=200)
TRASHMODE=$(zenity --list --text="trashmode:" --radiolist --column="Pick" --column="Opinion" --column="Description" FALSE "0" "No trashing" TRUE "1" "Files will be moved to trash RealFolder (255)" FALSE "2" "Files will be DELETED! (not undoable)" --width=500 --height=200)
(
    folder=$(pwd)
    for arg in "$@"
    do
        #filesize=$(stat -c%s "$arg")
        filesize=`stat -c %s $arg`
        if [ "$filesize" -gt 209715200 ]
        then
            echo "File $arg exceeds 200MB (filesize=$filesize)"
            echo "Creating temporary files: Adding $arg to $arg.rar..."
            (
                rar a -m3 -v209715200b -Idp -- "$arg".rar "$folder"/"$arg"
            ) | zenity --progress --text="Creating temporary files: Adding $arg to $arg.rar..." --percentage=0 --pulsate --auto-close --auto-kill
            echo "Temporary files created: Uploading temporary files..."
            (
                find "$folder" -iname "*$arg*.rar*" -exec rsapiresume.pl '{}' $TYPE $LOGIN $PASSWORD $UPDATEMODE $TRASHMODE \;
            ) | zenity --progress --text="Uploading temporary files..." --percentage=0 --pulsate --auto-close --auto-kill
            echo "Upload Completed: Deleting temporary files..."
            zenity --title="Upload Completed!" --question --text="Upload Completed!\nDelete temporary files?" --ok-label="YES" --cancel-label="NO"
            if [ "$?" -eq "0" ]
            then
                (
                find "$folder" -iname "*$arg*.rar*" -exec rm -v '{}' \;
                ) | zenity --progress --text="Deleting temporary files..." --percentage=0 --pulsate --auto-close --auto-kill
                echo "Temporary files deleted!"
            fi
        else
            echo "File $arg does not exceed 200MB (filesize=$filesize)"
            echo "Uploading $arg..."
            (
                find "$folder" -iname "$arg" -exec rsapiresume.pl '{}' $TYPE $LOGIN $PASSWORD $UPDATEMODE $TRASHMODE \;
            ) | zenity --progress --text="Uploading $arg..." --percentage=0 --pulsate --auto-close --auto-kill
            echo "Upload Completed"
            zenity --title="Upload Completed!" --info --text="Upload Completed!"
        fi
    done
    echo "Check rsapiuploads.txt to view links!"
    zenity --title="FINISHED!" --question --text="Check rsapiuploads.txt?" --ok-label="YES" --cancel-label="NO"
    if [ "$?" -eq "0" ]
    then
        gedit "$folder"/rsapiuploads.txt
    fi
    echo "You may close this window!"
) | zenity --title=RSU --text-info --width=500 --height=500
```



```
#!/usr/bin/perl

# Version 2.2.3 (21. Sep. 2009)
# RapidShare AG OpenSource Perl Uploader. For non-commercial use only. All rights reserved. USE AT YOUR OWN RISK!

# Features:
# - Uploading to free, collector's zone and premium zone.
# - Supports MD5 check after uploads to check if the upload worked.
# - Supports upload resume to continue aborted uploads. Upload needs to be completed within 24 hours.
# - Supports new RealFolders for premium and collector's accounts.
# - Supports uploading whole directories in RealFolders.
# - Supports update modes and trash modes to update remote files without changing file IDs.

# Syntax: rsapiresume.pl <filename/folder> <free|prem|col> [login] [password] [updatemode] [trashmode]

# Update=0: Traditional uploading. No duplicate checking.
# Update=1: The lowest file ID duplicate will be overwritten if MD5 differs. Other duplicates will be handled using the trash flag.

# Trash=0: No trashing.
# Trash=1: Files will be moved to trash RealFolder (255)
# Trash=2: Files will be DELETED! (not undoable)

# To upload a file, put this script on a Linux machine with perl installed and use the following syntax:
# perl rsapiresume.pl mytestfile.rar free        (this uploads mytestfile.rar as a free user)
# perl rsapiresume.pl archive.rar prem 334 test  (this uploads archive.rar to the premium zone of login 334 with password test)
# perl rsapiresume.pl a.rar col testuser mypw    (this uploads a.rar to the collector's zone of login testuser with password mypw)

# perl rsapiresume.pl prem myfolder 334 mypw 1 1
# This uploads the folder myfolder and all subfolders to the premium zone of login 334 with password mypw.
# Update=1 will not upload files already existing with same md5. Existing but different files will be overwritten without
# changing the download link. Multiple duplicates will be moved to the RealFolder 255 (Trash), because we set the trash value to 1.

use strict;
use warnings;
use Digest::MD5("md5_hex");
use Fcntl;
use IO::Socket;
use LWP::Simple;

my ($FILE, $TYPE, $LOGIN, $PASSWORD, $UPDATEMODE, %ESCAPES, $TRASHMODE, %PARENTANDNAME_REALFOLDER);

$/ = undef;
$SIG{PIPE} = $SIG{HUP} = 'IGNORE';
$FILE = $ARGV[0] || "";
$TYPE = $ARGV[1] || "";
$LOGIN = $ARGV[2] || "";
$PASSWORD = $ARGV[3] || "";
$UPDATEMODE = $ARGV[4] || 0;
$TRASHMODE = $ARGV[5] || 0;

unless ($TYPE) { die "Syntax: $0 <filename/folder> <free|prem|col> [login] [password] [updatemode] [trashmode]\n" }
unless (-e $FILE) { die "File not found.\n" }

if (-d $FILE) {
  unless ($LOGIN and $PASSWORD) { die "Folder upload not supported for anonymous uploads.\n" }

  print "Counting all folders and files in $FILE...\n";
  my ($numfiles, $numfolders, $numbytes) = &countfiles($FILE);
  printf("You want to upload $numfiles files in $numfolders folders having $numbytes bytes (%.2f MB)\n", $numbytes / 1000000);
  if ($numfiles > 1000) { die "More than 1000 files? You should not do that...\n" }
  if ($numfolders > 100) { die "More than 100 folders? You should not do that...\n" }
  if ($numbytes > 100_000_000_000) { die "More than 100 Gigabytes? You should not do that...\n" }

  print "Uploading folder $FILE...\n";
  &listrealfolders($TYPE, $LOGIN, $PASSWORD);
  &uploadfolder($FILE, $TYPE, $LOGIN, $PASSWORD);
} else {
  &uploadfile($FILE, $TYPE, $LOGIN, $PASSWORD);
}

print "All done.\n";
exit;





sub countfiles {
  my $dir = shift || die;

  my ($filename, $numfiles, $numfolders, $numbytes, $subnumfiles, $subnumfolders, $subnumbytes);

  foreach $filename (glob("$dir/*")) {
    if ($filename =~ /\.uploaddata$/) { next }

    if (-d $filename) {
      ($subnumfiles, $subnumfolders, $subnumbytes) = &countfiles($filename);
      $numfiles += $subnumfiles;
      $numfolders++;
      $numbytes += $subnumbytes;
    } else {
      $numfiles++;
      $numbytes += -s $filename || 0;
    }
  }

  return ($numfiles || 0, $numfolders || 0, $numbytes || 0);
}





sub uploadfolder {
  my $file = shift || die;
  my $type = shift || die;
  my $login = shift || "";
  my $password = shift || "";
  my $parent = shift || 0;

  my ($realfolder, $filename, $htmllogin, $htmlpassword, $htmlname, $mode);

  $realfolder = $PARENTANDNAME_REALFOLDER{"$parent,$file"} || 0;
  $mode = "existed";

  unless ($realfolder) {
    $htmllogin = &htmlencode($login);
    $htmlpassword = &htmlencode($password);
    $htmlname = &htmlencode($file);
    $realfolder = get("http://api.rapidshare.com/cgi-bin/rsapi.cgi?sub=addrealfolder_v1&type=$type&login=$htmllogin&password=$htmlpassword&name=$htmlname&parent=$parent") || "";
    if (not $realfolder or $realfolder =~ /^ERROR: /) { die "API Error occured: $realfolder\n" }
    $mode = "created";
    unless ($realfolder =~ /^\d+$/) { die "Error adding RealFolder: $realfolder\n" }
  }

  print "Folder $file resolved to ID $realfolder ($mode)\n";

  foreach $filename (glob("$file/*")) {
    if ($filename =~ /\.uploaddata$/) { next }
    if (-d $filename) { &uploadfolder($filename, $type, $login, $password, $realfolder) } else { &uploadfile($filename, $type, $login, $password, $realfolder) }
  }

  return "";
}





sub listrealfolders {
  my $type = shift || die;
  my $login = shift || die;
  my $password = shift || die;

  my ($htmllogin, $htmlpassword, $result, $realfolder, $parent, $name);

  $htmllogin = &htmlencode($login);
  $htmlpassword = &htmlencode($password);

  $result = get("http://api.rapidshare.com/cgi-bin/rsapi.cgi?sub=listrealfolders_v1&login=$htmllogin&password=$htmlpassword&type=$type") || "";
  if (not $result or $result =~ /^ERROR: /) { die "API Error occured: $result\n" }

  foreach (split(/\n/, $result)) {
    ($realfolder, $parent, $name) = split(/,/, $_, 3);
    $PARENTANDNAME_REALFOLDER{"$parent,$name"} = $realfolder;
  }

  return "";
}





sub finddupes {
  my $type = shift || die;
  my $login = shift || die;
  my $password = shift || die;
  my $realfolder = shift || 0;
  my $filename = shift || "";

  my ($header, $result, $htmllogin, $htmlpassword, $htmlfilename, $fileid, $size, $killcode, $md5hex, $serverid);

  $htmllogin = &htmlencode($login);
  $htmlpassword = &htmlencode($password);
  $htmlfilename = &htmlencode($filename);
  $result = get("http://api.rapidshare.com/cgi-bin/rsapi.cgi?sub=listfiles_v1&login=$htmllogin&password=$htmlpassword&type=$type&realfolder=$realfolder&filename=$htmlfilename&fields=size,killcode,serverid,md5hex&order=fileid") || "";

  if (not $result or $result =~ /^ERROR: /) { die "API Error occured: $result\n" }
  if ($result eq "NONE") { print "FINDDUPES: No dupe detected.\n"; return (0,0,0,0,0) }

  foreach (split(/\n/, $result)) {
    unless ($_ =~ /^(\d+),(\d+),(\d+),(\d+),(\w+)/) { die "FINDDUPES: Unexpected result: $result\n" }
    unless ($fileid) { $fileid = $1; $size = $2; $killcode = $3; $serverid = $4; $md5hex = lc($5); next }
    print "FINDDUPES: Deleting dupe $1\n";
    &deletefile($1, $3);
  }

  return ($fileid, $size, $killcode, $serverid, $md5hex);
}





sub deletefile {
  my $fileid = shift || die;
  my $killcode = shift || die;

  if ($TRASHMODE == 1) {
    print "DELETEFILE: Moving file $fileid to trash RealFolder 255.\n";
    my $result = get("http://api.rapidshare.com/cgi-bin/rsapi.cgi?sub=movefilestorealfolder_v1&files=f$fileid"."k$killcode&realfolder=255") || "";
    if ($result ne "OK") { die "DELETEFILE: Unexpected server reply: $result\n" }
  }

  elsif ($TRASHMODE == 2) {
    print "DELETEFILE: DELETING file $fileid.\n";
    my $result = get("http://api.rapidshare.com/cgi-bin/rsapi.cgi?sub=deletefiles_v1&files=f$fileid"."k$killcode") || "";
    if ($result ne "OK") { die "DELETEFILE: Unexpected server reply: $result\n" }
  }

  else {
    print "DELETEFILE: Doing nothing with file $fileid, because trash mode is 0.\n";
  }

  return "";
}





sub uploadfile {
  my $file = shift || die;
  my $type = shift || die;
  my $login = shift || "";
  my $password = shift || "";
  my $realfolder = shift || 0;

  my ($size, $filecontent, $md5hex, $size2, $uploadserver, $cursize, $dupefileid, $dupesize, $dupekillcode, $dupemd5hex);

# This chapter checks the file and calculates the MD5HEX of the existing local file.
  $size = -s $file || die "File $file is empty or does not exist!\n";
  print "File $file\n$size has byte. Full file MD5 is... ";
  open(FH, $file) || die "Unable to open file: $!\n";
  binmode(FH);
  $filecontent = <FH>;
  close(FH);
  $md5hex = md5_hex($filecontent);
  $size2 = length($filecontent);
  print "$md5hex\n";
  unless ($size == $size2) { die "Strange error: $size byte found, but only $size2 byte analyzed?\n" }

  if ($UPDATEMODE and $login and $password) {
    ($dupefileid, $dupesize, $dupekillcode, $uploadserver, $dupemd5hex) = &finddupes($type, $login, $password, $realfolder, $file);
    if ($md5hex eq $dupemd5hex) { print "FILE ALREADY UP TO DATE! Server rs$uploadserver.rapidshare.com in file ID $dupefileid.\n\n"; return "" }
    if ($dupefileid) { print "UPDATING FILE $dupefileid on server rs$uploadserver.rapidshare.com ($type)\n" }
  }

  unless ($uploadserver) {
    print "Getting a free upload server...\n";
    $uploadserver = get("http://api.rapidshare.com/cgi-bin/rsapi.cgi?sub=nextuploadserver_v1") || "";
    if (not $uploadserver or $uploadserver =~ /^ERROR: /) { die "API Error occured: $uploadserver\n" }
    print "Uploading to rs$uploadserver.rapidshare.com ($type)\n";
  }

  $cursize = 0;
  while ($cursize < $size) { $cursize = &uploadchunk($file, $type, $login, $password, $realfolder, $md5hex, $size, $cursize, "rs$uploadserver.rapidshare.com:80", $dupefileid, $dupekillcode) }

  return "";
}





sub uploadchunk {
  my $file = shift || die;
  my $type = shift || die;
  my $login = shift || "";
  my $password = shift || "";
  my $realfolder = shift || 0;
  my $md5hex = shift || die;
  my $size = shift || die;
  my $cursize = shift || 0;
  my $fulluploadserver = shift || die;
  my $replacefileid = shift || 0;
  my $replacekillcode = shift || 0;

  my ($uploaddata, $wantchunksize, $fh, $socket, $boundary, $contentheader, $contenttail, $contentlength, $header, $chunks, $chunksize,
$bufferlen, $buffer, $result, $fileid, $complete, $resumed, $filename, $killcode, $remotemd5hex, $chunkmd5hex);

  if (-e "$file.uploaddata") {
    open(I, "$file.uploaddata") or die "Unable to open file: $!\n";
    ($fulluploadserver, $fileid, $killcode) = split(/\n/, <I>);
    print "RESUMING UPLOAD! Uploadserver=$fulluploadserver\nFile-ID=$fileid\nKillcode=$killcode\n";
    close(I);
    print "Requesting authorization for upload resume...\n";
    $cursize = get("http://api.rapidshare.com/cgi-bin/rsapi.cgi?sub=checkincomplete_v1&fileid=$fileid&killcode=$killcode") || "";
    unless ($cursize =~ /^\d+$/) { die "Unable to resume! Please delete $file.uploaddata or try again.\n" }
    print "The upload stopped at $cursize on server $fulluploadserver.\n";
    $resumed = 1;
  }

  $wantchunksize = 1000000;

  if ($size > $wantchunksize) {
    $chunks = 1;
    $chunksize = $size - $cursize;
    if ($chunksize > $wantchunksize) { $chunksize = $wantchunksize } else { $complete = 1 }
  } else {
    $chunks = 0;
    $chunksize = $size;
  }

  print "Upload chunk is $chunksize byte starting at $cursize.\n";

  sysopen($fh, $file, O_RDONLY) || die "Unable to open file: $!\n";
  $filename = $file =~ /[\/\\]([^\/\\]+)$/ ? $1 : $file;
  $socket = IO::Socket::INET->new(PeerAddr => $fulluploadserver) || die "Unable to open socket: $!\n";
  $boundary = "---------------------632865735RS4EVER5675865";
  $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="rsapi_v1"\r\n\r\n1\r\n|;

  if ($resumed) {
    $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="fileid"\r\n\r\n$fileid\r\n|;
    $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="killcode"\r\n\r\n$killcode\r\n|;
    if ($complete) { $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="complete"\r\n\r\n1\r\n| }
  } else {
    if ($type eq "prem" and $login and $password) { $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="login"\r\n\r\n$login\r\n| }
    if ($type eq "col" and $login and $password) { $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="freeaccountid"\r\n\r\n$login\r\n| }

    $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="password"\r\n\r\n$password\r\n|;
    $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="realfolder"\r\n\r\n$realfolder\r\n|;
    $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="replacefileid"\r\n\r\n$replacefileid\r\n|;
    $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="replacekillcode"\r\n\r\n$replacekillcode\r\n|;

    if ($chunks) { $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="incomplete"\r\n\r\n1\r\n| }
  }

  $contentheader .= qq|$boundary\r\nContent-Disposition: form-data; name="filecontent"; filename="$filename"\r\n\r\n|;
  $contenttail = "\r\n$boundary--\r\n";
  $contentlength = length($contentheader) + $chunksize + length($contenttail);

  if ($resumed) {
    $header = qq|POST /cgi-bin/uploadresume.cgi HTTP/1.0\r\nContent-Type: multipart/form-data; boundary=$boundary\r\nContent-Length: $contentlength\r\n\r\n|;
  } else {
    $header = qq|POST /cgi-bin/upload.cgi HTTP/1.0\r\nContent-Type: multipart/form-data; boundary=$boundary\r\nContent-Length: $contentlength\r\n\r\n|;
  }

  print $socket "$header$contentheader";

  sysseek($fh, $cursize, 0);
  $bufferlen = sysread($fh, $buffer, $wantchunksize) || 0;
  unless ($bufferlen) { die "Error while reading file: $!\n" }
  $chunkmd5hex = md5_hex($buffer);
  print "Sending $bufferlen byte...\n";
  $cursize += $bufferlen;
  print $socket $buffer;
  print $socket $contenttail;
  print "Reading server response...\n";
  ($result) = <$socket> =~ /\r\n\r\n(.+)/s;
  unless ($result) { die "Ooops! Did not receive any valid server results?\n" }

  if ($resumed) {
    if ($complete) {
      if ($result =~ /^COMPLETE,(\w+)/) {
        print "Upload completed! Remote MD5=$1 Local MD5=$md5hex\n";
        if ($md5hex ne $1) { die "MD5 CHECK NOT PASSED!\n" }
        print "MD5 check passed. Upload OK! Saving status to rsapiuploads.txt\n\n";
        unlink("$file.uploaddata");
      } else {
        die "Unexpected server response!\n";
      }
    } else {
      if ($result =~ /^CHUNK,(\d+),(\w+)/) {
        print "Chunk upload completed! $1 byte uploaded.\nRemote MD5=$2 Local MD5=$chunkmd5hex\n\n";
        if ($2 ne $chunkmd5hex) { die "CHUNK MD5 CHECK NOT PASSED!\n" }
      } else {
        die "Unexpected server response!\n\n$result\n";
      }
    }
  } else {
    if ($result =~ /files\/(\d+)/) { $fileid = $1 } else { die "Server result did not contain a file ID.\n" }
    unless ($result =~ /File1\.3=(\d+)/ and $1 == $cursize) { die "Server did not save all data we sent.\n" }
    unless ($result =~ /File1\.2=.+?killcode=(\d+)/) { die "Server did not send our killcode.\n" }
    $killcode = $1;
    unless ($result =~ /File1\.4=(\w+)/) { die "Server did not send the remote MD5 sum.\n" }
    $remotemd5hex = lc($1);

    if ($chunks) {
      if ($result !~ /File1\.5=Incomplete/) { die "Server did not acknowledge the incomplete upload request.\n" }
      print "Chunk upload completed! $cursize byte uploaded.\nRemote MD5=$remotemd5hex Local MD5=$chunkmd5hex\n";
      if ($remotemd5hex ne $chunkmd5hex) { die "CHUNK MD5 CHECK NOT PASSED!\n" }
      print "Upload OK! Saving to rsapiuploads.txt and resuming upload...\n\n";
      open(O, ">$file.uploaddata") or die "Unable to save upload server: $!\n";
      print O "$fulluploadserver\n$fileid\n$killcode\n";
      close(O);
    } else {
      if ($result !~ /File1\.5=Completed/) { die "Server did not acknowledge the completed upload request.\n" }
      if ($md5hex ne $remotemd5hex) { die "FINAL MD5 CHECK NOT PASSED! LOCAL=$md5hex REMOTE=$remotemd5hex\n" }
      print "FINAL MD5 check passed. Upload OK! Saving status to rsapiuploads.txt\n$result";
    }

    open(O,">>rsapiuploads.txt") or die "Unable to save to rsapiuploads.txt: $!\n";
    print O $chunks ? "Initialized chunk upload for file $file.\n$result" : "Uploaded file $file.\n$result";
    close(O);
  }

  return $cursize;
}





sub htmlencode {
  my $text = shift || "";

  unless (%ESCAPES) {
    for (0 .. 255) { $ESCAPES{chr($_)} = sprintf("%%%02X", $_) }
  }

  $text =~ s/(.)/$ESCAPES{$1}/g;

  return $text;
}
```

I tried to enable file selection through gui in the case of calling the script with no file selected...couldn't do it...but will keep trying!

cheers

---

### Post by joselol on 2009-11-13
Updated script:

now checks if upload was completed by checking the presence of *.uploaddata

```
#!/bin/bash
# Right-click upload files to your rapidshare account
# Owner: 
#   José Lourenço
#   joselol1987@gmail.com
# Licence: GNU GPL
# Based on RapidUpload - Anand Kapre - ak@anandkapre.com
# Dependency:
#   rar zenity nautilus gnome2 rsapiresume.pl
# Created on Tuesday November 10th 2009
# Tested on Ubuntu
TYPE=$(zenity --list --text="account:" --radiolist --column="Pick" --column="Opinion" --column="Description" FALSE free "free zone" FALSE prem "premium zone" TRUE col "collector's zone" --width=500 --height=200)
LOGIN=$(zenity --entry --text="username:" --entry-text="username" --width=500)
PASSWORD=$(zenity --entry --text="password:" --entry-text="password" --hide-text --width=500)
UPDATEMODE=$(zenity --list --text="updatemode:" --radiolist --column="Pick" --column="Opinion" --column="Description" FALSE "0" "Traditional uploading, no duplicate checking" TRUE "1" "The lowest file ID duplicate will be overwritten if MD5 differs>" --width=500 --height=200)
TRASHMODE=$(zenity --list --text="trashmode:" --radiolist --column="Pick" --column="Opinion" --column="Description" FALSE "0" "No trashing" TRUE "1" "Files will be moved to trash RealFolder (255)" FALSE "2" "Files will be DELETED! (not undoable)" --width=500 --height=200)
(
    folder=$(pwd)
    for arg in "$@"
    do
        #filesize=$(stat -c%s "$arg")
        filesize=`stat -c %s "$arg"`
        if [ "$filesize" -gt 209715200 ]
        then
            echo "File $arg exceeds 200MB (filesize=$filesize)"
            echo "Creating temporary files: Adding $arg to $arg.rar..."
            (
                rar a -m3 -v209715200b -Idp -- "$arg".rar "$folder"/"$arg"
            ) | zenity --progress --text="Creating temporary files: Adding $arg to $arg.rar..." --percentage=0 --pulsate --auto-close --auto-kill
            echo "Temporary files created: Uploading temporary files..."
            (
                find "$folder" -iname "*$arg*.rar*" -exec rsapiresume.pl '{}' $TYPE $LOGIN $PASSWORD $UPDATEMODE $TRASHMODE \;
            ) | zenity --progress --text="Uploading temporary files..." --percentage=0 --pulsate --auto-close --auto-kill
            datafiles=`find "$folder" -iname "*$arg*.uploaddata"`
            while [ -n "$datafiles" ]
            do
                echo "RE-Uploading temporary files..."
                (
                    find "$folder" -iname "*$arg*.rar*" -exec rsapiresume.pl '{}' $TYPE $LOGIN $PASSWORD $UPDATEMODE $TRASHMODE \;
                ) | zenity --progress --text="RE-Uploading temporary files..." --percentage=0 --pulsate --auto-close --auto-kill
                datafiles=`find "$folder" -iname "*$arg*.uploaddata"`
            done
            echo "Upload Completed: Deleting temporary files..."
            zenity --title="Upload Completed!" --question --text="Upload Completed!\nDelete temporary files?" --ok-label="YES" --cancel-label="NO"
            if [ "$?" -eq "0" ]
            then
                (
                find "$folder" -iname "*$arg*.rar*" -exec rm -v '{}' \;
                ) | zenity --progress --text="Deleting temporary files..." --percentage=0 --pulsate --auto-close --auto-kill
                echo "Temporary files deleted!"
            fi
        else
            echo "File $arg does not exceed 200MB (filesize=$filesize)"
            echo "Uploading $arg..."
            (
                find "$folder" -iname "$arg" -exec rsapiresume.pl '{}' $TYPE $LOGIN $PASSWORD $UPDATEMODE $TRASHMODE \;
            ) | zenity --progress --text="Uploading $arg..." --percentage=0 --pulsate --auto-close --auto-kill
            datafile=`find "$folder" -iname "$arg.uploaddata"`
            while [ -n "$datafile" ]
            do
                echo "RE-Uploading $arg..."
                (
                    #rsu.jlol.pl "${datafile%.*a}"
                    find "$folder" -iname "$arg" -exec rsapiresume.pl '{}' $TYPE $LOGIN $PASSWORD $UPDATEMODE $TRASHMODE \;
                ) | zenity --progress --text="RE-Uploading temporary files..." --percentage=0 --pulsate --auto-close --auto-kill
                datafile=`find "$folder" -iname "$arg.uploaddata"`
            done
            echo "Upload Completed"
            zenity --title="Upload Completed!" --info --text="Upload Completed!"
        fi
    done
    echo "Check rsapiuploads.txt to view links!"
    zenity --title="FINISHED!" --question --text="Check rsapiuploads.txt?" --ok-label="YES" --cancel-label="NO"
    if [ "$?" -eq "0" ]
    then
        gedit "$folder"/rsapiuploads.txt
    fi
    echo "You may close this window!"
) | zenity --title=RSU --text-info --width=500 --height=500
```

---

### Post by Ciwan on 2009-11-24
Hmm I do not to right click a file and choose upload to Upload it to RS.

I was hoping for something exactly like RapidUploader (from RS website for Windows).

Where all I have to do is Drag & Drop my RARs into the program and that is it ! No more worries.

With this script that you guys currently have .. I take it you can not place passwords on your RAR Files ! Like you do with WinRAR on Windows. Or can you ?

On Windows I first RAR my files with WinRAR, then open up RapidUploader > Sign in with my Premium Account > then Drag & Drop RAR files to upload.

I hope we had something like this for Ubuntu, this way I would never go back to Windows.

---

### Post by arst06d on 2009-11-26
I've just tried Rapiduploader and it works fine under Karmic Koala ....

---

### Post by AnotherNoob on 2009-12-07
is there any way to open more connections at one time i mean 10 simultaneous connections , like RS uploader ??

---

### Post by Deichscheich on 2010-05-18
Great work so far, but wouldn't it be great if the script would automatically create .rar-archives in one specified folder before uploading and deleting them? I am thinking about backing up my music collection - I would need seperate archives for each artist.

---

