---
title: "Nautilus script/extension for sorting trash by date deleted"
date: 2009-06-05
forum: General Help
---

### Post by Altay_H on 2009-06-05
I'm interested in viewing the items in sorting the items in my trash folder by date deleted. I'm tired of waiting for Ubuntu to do this, and it seems like a simple enough task, so I'm wondering if there's any way to do it with a Nautilus script or extension.
1. Has someone already written a script/extension to do this?
2. Assuming no one has done so, will it be difficult to create one?

I was unable to find any scripts or extensions for nautilus that would do what I want, so I'm going to assume one has not been written. I have a decent amount of experience in C++ and have written quite a few Perl scripts, so I figure I might be able to do this with some help.

I can't imagine this being too difficult, because in the folder ~/.local/share/Trash/info/ there are data for each file in the Trash folder with the contents:
```
[Trash Info]
Path=/path/where/file/was/located/when/deleted/file.ext
DeletionDate=YYYY-MM-DDTHH:MM:SS
```

Essentially all the script would have to do is create a hash of the filenames and deletion dates, sort them by deletion date, then output the filenames in the correct order. The problem is that I don't have any idea how to tell nautilus to arrange the files once I have the filenames in the correct order. Am I going about this the wrong way? Thanks for any help!

---

### Post by tk03759 on 2009-07-03
For a while, I thought my trash was doing this, but then I realized that the dates I was seeing were the Last Modified dates. I think this is unusual and unexpected behaviour, especially for new users.

Adding this functionality, even if only in a script, would be really beneficial. I'll try looking stuff up. I've only ever made simple scripts though, so if anyone else has any ideas it would help. ;)

__

Edit: According to Ubuntu Package "trash-cli": "This package provides a command line interface trashcan utility compliant with the FreeDesktop.org Trash Specification. It remembers the name, original path, deletion date, and permissions of each trashed file."

If these things are recorded there is definitely a way of doing this.

This issue is also listed as a bug: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/301552]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/301552")

---

### Post by Altay_H on 2009-07-03
> **tk03759 said:**
> Adding this functionality, even if only in a script, would be really beneficial. I'll try looking stuff up. I've only ever made simple scripts though, so if anyone else has any ideas it would help. ;)
It's nice to hear that I'm not the only one who wants this functionality. :)

> **tk03759 said:**
> It remembers the name, original path, deletion date, and permissions of each trashed file."
I actually mentioned this in my previous post. You can see the details of each file in ~/.local/share/Trash/info/.

> **tk03759 said:**
> If these things are recorded there is definitely a way of doing this.
Indeed. I have no doubt that it's possible to do; I just wonder if anyone who cares will ever do it. I'm sure I can write a Nautilus script which organizes the file names into the correct order. My problem is that I have no idea how to force the icons to organize themselves into that order. All I can do is output a list of the filenames in the correct order. If you think this could be useful I might actually write the script and upload it. Otherwise, I think we might need to mess with the source code of Nautilus to make this work.

> **tk03759 said:**
> This issue is also listed as a bug: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/301552]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/301552")
It's always nice to see a problem in the bugs list, but I doubt it will actually be implemented anytime soon. I've been waiting for this to be fixed ever since I first started using Ubuntu. Anyway, it's more of a feature request than a bug.

---

### Post by Altay_H on 2009-07-08
I wrote a Perl script which organizes the files by date deleted and prints a list. I'll attach the script to this post and also paste it below. If anyone knows a way to use the output of this file to control the order in which Nautilus places the files please let me know.

```
#!/usr/bin/perl
use warnings;
use strict;

# Create an alphabetical listing of all the files and folders in the Trash
my @files = `ls ~/.local/share/Trash/files`;

# Create a hash to store the corresponding DeletionDates to each file
my %file_hash;

# Iterate once for each file in the array
for(my $i = 0; $i <= $#files; $i++)
{
	# Remove all linebreaks and replace all " " with "\ "
	$files[$i] =~ s/\n//g;
	$files[$i] =~ s/ /\\ /g;
	
	# Find the trashinfo for the current file
	my $fileinfo = `cat ~/.local/share/Trash/info/$files[$i].trashinfo`;
	
	# Uncomment the next line for the output to use " " instead of "\ "
	#$files[$i] =~ s/\\ / /g;
	
	# Extract the DeletionDate from the trashinfo of the file
	# The following three lines could probably be condensed into one or two
	my $DeletionDate = $fileinfo;
	$DeletionDate =~ s/DeletionDate=(.+)/$1/;
	$DeletionDate = $1;
	
	# Store the information in the hash for later use
	$file_hash{"$DeletionDate"} = $files[$i];
}

# Sort and print the files in the hash
# Note: This will sort the files from OLDEST TO NEWEST
foreach my $key (sort (keys(%file_hash)))
{
	print("$file_hash{$key}\n");
}


# USE FOR DEBUGGING TO PRINT A PRETTY HASH
#foreach my $key (sort (keys(%file_hash))) {
#	print "\t\t$key \t\t$file_hash{$key}\n";
#}

```

---

### Post by sancho panza on 2009-08-04
@Altay: The package tk suggested is "trash-cli" which is a command line tool seperate from what you are talking about. It has more features than what you can find in the trash/info folder. [More here]("http://code.google.com/p/trash-cli/") and [here]("http://www.ramendik.ru/docs/trashspec.html").

There is also some code used in KDE in [this bugreport.]("https://bugs.launchpad.net/nautilus/+bug/228369/comments/6").
Cheers!

---

### Post by sancho panza on 2009-08-07
I've listed a set of [bugreports here]("http://ubuntuforums.org/showthread.php?t=1233173").

Maybe someone who knows coding can put something together using the KDE bugfix mentioned in the last post and/or the trash-cli program?

---

### Post by Krallus on 2009-09-06
I just ran into this myself and my searching lead me here.  Anyway, after a bit of experimenting, here are a couple of quick and easy commands, from the shell, that will likely give you what you're looking for:

$ ls -cltr ~/.local/share/Trash/files

(if you have trouble remembering the list of options, think of how you want to sort through your "clutter"..heh .. of course, you could just make it a command alias in your shell like 'showtrash' or something like that)

OR

$ grep -hB 1 yyyy-mm-ddThh ~/.local/share/Trash/info/*

For example grep -hB 1 2009-09-06T14 ~/.local/share/Trash/info/* will list files deleted September 6 between 2:00 and 2:59 pm.

I agree, though: a "date deleted column" in Nautilus would be ideal.

---

### Post by sancho panza on 2009-09-07
Thanks for the tips, but these commands only sort them by date, but offer no way to delete them. How can I do that? Also, I doubt if the "ls" command you suggested sorts files by date deleted. I think it sorts them by modif/access date, which may not be the same as the delete date.

You could go to the bugreports I listed in my earlier post and push for this feature to get included. It is already implemented in KDE.

---

### Post by Krallus on 2009-09-07
The ls command I mentioned will sort by "ctime" (time of last modification of file status information) which includes when the file moved to its current directory, if that was the last change to the file status.  This use of the command presumes that the last change to the files of concern is the move to the trash folder, which I think is a reasonable assumption.

Deleting is something else .. though you could some funky things with chaining commands to delete a subset of the generated list, but I haven't bothered to figure out what that would be as, in my case, I just wanted to know the last couple of files I moved to the trash (and then changed my mind about), then looked for them by filename in the trash GUI and restored them.

I'll definitely bump the feature request.

---

### Post by sancho panza on 2009-10-22
There seems to be some incremental progress [here]("https://bugs.launchpad.net/nautilus/+bug/301552"). Screenshot is attached.
I could not get it to compile on my system as I'm a not familiar with checking dependencies and stuff. If others could help bump the bug, that might help.

Cheers,

[IMG]http://launchpadlibrarian.net/31759573/trash-deleted.png[/IMG]

---

### Post by opticyclic on 2009-11-29
Of course the other thing that hasn't been mentioned is also displaying the full path of the original location of the deleted file.
This can be just as useful as the date deleted in finding the relevant files.

EDIT: Seems like it HAS been addressed
[https://bugzilla.gnome.org/show_bug.cgi?id=89706](https://bugzilla.gnome.org/show_bug.cgi?id=89706)
[img]http://bugzilla-attachments.gnome.org/attachment.cgi?id=143484[/img]

---

### Post by sancho panza on 2009-11-29
It may have been fixed upstream, but it isnt fixed for regular users like me unless it turns up in some repository. Looks like it'll take ages to trickle down to regular users. Talk about red tape.

---

### Post by sancho panza on 2009-12-23
The voting system in Launchpad is now improved. You can vote on bugs that are important to you by clicking on the "This bug affects xx people. Does this bug affect you?" link in each bugreport.

Vote on the bug discussed in this thread by going to this page:
[https://bugs.launchpad.net/nautilus/+bug/301552]("https://bugs.launchpad.net/nautilus/+bug/301552")

Cheers!

---

### Post by opticyclic on 2010-04-30
Lucid Lynx has been released and I still don't see this functionality.

According to the Register, Chief operating officer and blogger Matt Asay said:
"I guarantee you will be impressed with Lucid if you look at it today,"
[http://www.theregister.co.uk/2010/04/27/ubuntu_10_04_mac_windows/](http://www.theregister.co.uk/2010/04/27/ubuntu_10_04_mac_windows/)

I'm certainly not impressed that such simple functionality (with a fix available) has been left out!  :evil: [-(

---

### Post by cozman69 on 2012-06-27
Just an update: This functionality is available in Linux Mint 13 and most likely in Ubuntu 12.04 (Precise Pangolin) since that's what Mint 13 is based on.  The Nautilus version is 3.4.2.

---

### Post by overdrank on 2012-06-27
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

