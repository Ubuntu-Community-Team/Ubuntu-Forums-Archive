---
title: "Gnome samba share handling does not work..."
date: 2008-05-22
forum: Desktop Environments
---

### Post by stiffmaster on 2008-05-22
I'm trying to play videos over samba, nothing fancy. I open nautilus double click on the file and it download who knows what at 60 KB/s on the network and nerver start playback ... And the worst part is, that if I browse to the ~/.gvfs/share on server/ (which is the gvfs mountpoint for my share) and double click, well it plays just fine ?!? Can anyone please explain me how I can fix this? 

I was thinking of replacing the totem executable by a script that would parse the parameter and change smb://server/share/file by ~/.gvfs/share on server/file but lets face it... This is a very ugly patch. I mean samba has been around forever. This should work out of the box right?!

---

### Post by stiffmaster on 2008-05-26
Well since I got no answers I went ahead and built the actual script that replace smb:// with a link to the gvfs file system and now everything works great .. 

Here for those interested:
```
#!/usr/bin/perl -w

########################################################
# This script replace smb:// urls to use gnome gvfs    #
# You can now play videos using nautilus double click!!#
#                                                      #
#         By Steve Garon                               #
########################################################

#Initialise arguments
my $home = $ENV{'HOME'};
my $file = "";
my $path = "";
my $executable = "totem.bin";
my $checkgvfs = 0;

#Check all arguments
foreach $num (0 .. $#ARGV){
	#Check if this is a samba link
	if ($ARGV[$num] =~ m/^smb:\/\/(\w+)\/(\w+)(\/.+)/){
		#Change the path to use gvfs
		$path = "$home/.gvfs/".$2."\\ on\\ ".$1;
		$file = $path.$3;
		$file = "file://".$file;
		$checkgvfs = 1;
	}
	else {	
		#Don't Change the arguments cause as far as I know everything else works
		$file = $ARGV[$num];
	}
}

#Check the GVFS mount point to see if it exist
if ($checkgvfs==1){
	#if doesnt exist
	unless(-e $path){
		#unmount gvfs mount point and restart fuse deamon
		system("/bin/fusermount -u ~/.gvfs &");
		system("/usr/lib/gvfs/gvfs-fuse-daemon -d ~/.gvfs &");
	}
}

#Start totem with the passed arguments
exec $executable." ".$file;
```

NOTES: 
(1) You have to move /usr/bin/totem to /usr/bin/totem.bin 
(2) You have to put the script as /usr/bin/totem

PS.: If you do have other Ideas, fell free to share!

---

