---
title: "What do i do about debsums: checksum mismatch?"
date: 2005-10-29
forum: Desktop Environments
---

### Post by seatea on 2005-10-29
I have been trying out Ubuntu and in the process installing  and removigng programs, notably a failed attempt to get RealPlayer to work on my computer, and wondering  if I have messed anything up in the process. I have previously only used Mac OS 9.2.2, so the transition to Ubuntu has been a little rough and I still feel like I am knocking  around in the dark. I saw this section in a Linux users book about  debsums and I decided I  would run the program. I got mostly ok output, but there were some problems I don't know how to interpret. Here's a sample:

"debsums: checksum mismatch capplets-data file /usr/share/applications/mimeinfo.cache
debsums: no md5sums for console-data
debsums: no md5sums for cpio
debsums: no md5sums for dc
debsums: no md5sums for debianutils
debsums: no md5sums for doc-base
debsums: no md5sums for doc-debian
debsums: no md5sums for dosfstools
debsums: no md5sums for ed
debsums: checksum mismatch firefox file       /usr/lib/mozilla-firefox/res/platform-forms.css" .

My source book said not to be concerned about md5sums,- what are these anyway?- which  was most of the output, but I am more concerned about the checksum mismatch incidents. Where is the  file that debsums is using for comparison and how is it generated? Can I simply  reinstall the  problematic files or  programs and correct these  errors or do I need to do more?  

Thanks.

---

### Post by seatea on 2005-10-31
I hope no one  takes offense that I bumped this post.  I am still looking for an answer.

---

### Post by felix_stegerman on 2005-10-31
[QUOTE=seatea]Here's a sample:

"debsums: checksum mismatch capplets-data file /usr/share/applications/mimeinfo.cache
debsums: no md5sums for console-data
debsums: no md5sums for cpio
debsums: no md5sums for dc
debsums: no md5sums for debianutils
debsums: no md5sums for doc-base
debsums: no md5sums for doc-debian
debsums: no md5sums for dosfstools
debsums: no md5sums for ed
debsums: checksum mismatch firefox file       /usr/lib/mozilla-firefox/res/platform-forms.css" .

My source book said not to be concerned about md5sums,- what are these anyway?- which  was most of the output
[/QUOTE]

> 
Wikipedia says:
In cryptography, MD5 (Message-Digest algorithm 5) is a widely-used cryptographic hash function with a 128-bit hash value. As an Internet standard (RFC 1321), MD5 has been employed in a wide variety of security applications, and is also commonly used to check the integrity of files.


[QUOTE=seatea]
but I am more concerned about the checksum mismatch incidents. Where is the  file that debsums is using for comparison and how is it generated? Can I simply  reinstall the  problematic files or  programs and correct these  errors or do I need to do more?
[/QUOTE]

Most packages provide a md5sums file (placed in /var/lib/dpkg/info),
which contains the md5 hashes (created with the md5sum utility),
to allow checking the integrity of installed files. Some packages don't, which
is why you get "no md5sums for <package>" errors.

The "checksum mismatch" errors are normal for cache files and other files
modified during normal system usage.

If you want to, you can reinstall some affected packages, but unless you
think some of the files reported to mismatch should not have been modified,
there shouldn't be any problems.

You could post the entire output of `debsums -s' here, so I can take a look
at it, if that makes you feel any better ;-)


Felix

---

### Post by seatea on 2005-11-01
Thanks  for the information. I have been doing quite a bit of alterations of files from the command line following recommendations  from the forums and my reference sources as I have  tried to get my Ubuntu system set up. This has made me a little uncomfortable because I am not sure what is going to cause a major problem or just an incidental problem in the  Ubuntu  system. I knew prettty much what files to mess with and which ones need to be left alone in my Mac OS. With Ubuntu, as I indicated when I posted, I'm not clear on what the guidelines are yet. Interestingly, the output from the debsums check only showed a few mismatches in things I wasn't even thinking I had altered with the command line. None of them were from the system. I just wasn't sure what kind of importance they were. I think I will ignore  them for now.

---

### Post by felix_stegerman on 2005-11-01
Hi,

I do a lot of tinkering with my (Debian & Ubuntu) systems.
What I found to come in very handy, was my "backup" bash script.
A simple "backup <filename>" will copy <filename> to <filename>.0
(or .1 if .0 exists), which makes for very easy backups.
And beause it's so fast, it's easy to make a habit out of it.

e.g.

# cd /etc/
# sudo backup some_config_file
# sudo edit some_config_file

If you call "backup <dir>" it creates a tar archive: <dir>.bak.0.tar
The best place to put it would be /usr/local/bin,
so you can also use it as root through sudo.

I put my entire /usr/local/bin (w/ some other handy dpkg/apt scripts)
into a tar.bz2 archive attached.


Felix

--

Edit: just found a bug in the forums. my signature goes to the top
of the post when I attach a file ;-) ... and I fixed a typo

---

### Post by seatea on 2005-11-02
[QUOTE=felix_stegerman]

"If you call "backup <dir>" it creates a tar archive: <dir>.bak.0.tar
The best place to put it would be /usr/local/bin,
so you can also use it as root through sudo.

I put my entire /usr/local/bin (w/ some other handy dpkg/apt scripts)
into a tar.bz2 archive attached."


Felix,

Thanks for the suggestion. I have a reference book that only vaguely comments on the  "usr" directory. What is your general take on its contents? Also, in  Linux  what does "bin"  generally mean when applied to a folder? I had thought it refered to an application  file or folder, but  it seems to be more commonly used than that. And finally, what do you mean by "archive attached"?

 I apologize for the elementary questions. Having only used a Macintosh system for so long, I still haven't adapted to the Linux file system. I realized this all the more  the other day when I was trying to type out a file path. Lots of new rules...

seatea

---

### Post by felix_stegerman on 2005-11-03
[QUOTE=seatea]
Thanks for the suggestion. I have a reference book that only vaguely comments on the "usr" directory. What is your general take on its contents? Also, in  Linux what does "bin" generally mean when applied to a folder? I had thought it refered to an application file or folder, but it seems to be more commonly used than that. And finally, what do you mean by "archive attached"?

I apologize for the elementary questions. Having only used a Macintosh system for so long, I still haven't adapted to the Linux file system. I realized this all the more the other day when I was trying to type out a file path. Lots of new rules...
[/QUOTE]

The Filesystem Hierarchy Standard at
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
can tell you all about the various parts of the file system.
You don't have to read it in its entirity (as I did).
You can get the general idea by reading the discriptions.

And by "archive attached" I mean the file attached to my last post.
At the bottom of that post it says: "Attached Files: _usr_local_bin.tar.bz2".
There's a link to a tar.bz2 archive that contains the files I mentioned.


Felix

---

