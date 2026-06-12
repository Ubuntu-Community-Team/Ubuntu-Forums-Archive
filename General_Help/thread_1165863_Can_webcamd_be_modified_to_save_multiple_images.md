---
title: "Can webcamd be modified to save multiple images?"
date: 2009-05-21
forum: General Help
---

### Post by Razmear on 2009-05-21
I've got webcamd setup to ftp pics to my webserver, but it seems to only be able to save the latest image on the server by default. Can the perl script be modified so that the webcam.jpg filename can be incremented by one every time it takes a pic?

My goal is not to have these images viewable to the world, so having the latest pic be numbered lowest is not needed like most webcam softwares want to do. Just increasing the image name by one is sufficent for my needs and I can review the pics later as needed. 

The reason for this request is one of my neighbors ran off someone trying to climb into my living room window while I was away last week, so I want to capture a pic every 30 seconds and if I should come home and find my house ransacked then be able to go to my FTP server and download the pics to see if I caught the ******* on the vid. webcamd seems to be the lightest system load of the webcam upload programs, but lacks the essential feature of being able to save multiple images. It looks like a simple edit to the perl script would be able to pull this off, but I haven't played with perl in many years, so maybe someone can help me out a bit. 

Here is the code where the output happens: 

```

#On écrit le fichier
    my $filename = "$home/.webcamd/webcam.jpg";
    open(DATA, ">$filename") or die "can't open $filename\n";
         $image->Write(file=>DATA, filename=>$filename); 
    close(DATA);
}

sub move_file()
{
    if($enable_ftp eq "yes")
    {
	$filename = "$home/.webcamd/webcam.jpg";
	$trans_mode = "I";
	&upload($filename,$trans_mode);
    }
    else
    {
	system("mv $home/.webcamd/webcam.jpg $www_path/webcam.jpg");
    }
}

```


Thanks for any help you can offer, also suggestions of other apps would be appreciated if this code can't be modified effectively. 

eb

---

