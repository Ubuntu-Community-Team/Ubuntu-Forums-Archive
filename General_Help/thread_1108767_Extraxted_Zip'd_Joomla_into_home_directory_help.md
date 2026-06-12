---
title: "Extraxted Zip'd Joomla into home directory help"
date: 2009-03-28
forum: General Help
---

### Post by Toady00 on 2009-03-28
I have xampp and I was trying to install Joomla and I accidently unzipped it in my home directory instead of /opt/lampp/htdocs/joomla is there a way to clean up my home directory? As soon as i did it I tried to view my home dir by date and there wasn't anything there from today but I know some of the folders didn't exist before.

---

### Post by ryanhaigh on 2009-03-28
From [here]("http://articles.techrepublic.com.com/5100-10878_11-1035686.html"):
> Undo a tar extraction
If you extract a huge tar archive to the wrong location, here's an easy way to undo the operation. Suppose you've just run the tar command to extract the files from an archive named tons_of_files.tar. By default, the tar utility extracts the files to an archive created one directory below the working directory. Here's the command you run to extract the archive:
tar -xvf tons_of_files.tar

Now, suppose you realize that you really didn't want to extract all those files to a directory positioned one level below the current directory. Fine, but what do you do about all those extraneous files? The following command uses the xargs utility to remove the files you just extracted. It works by using the tar command to list the files; the list is then passed via a pipe to xargs, which runs the rm command on each of the extracted files. Here's the command:
tar -tf tons_of_files.tar | xargs rm

After you run this command, the extracted files will be gone

I haven't tested this myself but I might suggest that you use try the command using echo first to ensure it isn't going to remove any files you want yo keep.

```
tar -tf tons_of_files.tar | xargs echo
```

---

