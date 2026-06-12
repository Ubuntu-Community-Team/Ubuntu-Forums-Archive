---
title: "Beginner question on users ..."
date: 2009-03-19
forum: General Help
---

### Post by fabianus on 2009-03-19
Hello all !

I would like to know how to deal with this : 

I installed my ubuntu server 8.10 with an admin account called fabianus. I installed a website on it (a magento shop). Now, the admin has to upload from time to time a file which magento uses in order to import products. He does this by ftp. in order to connect to the ftp server he uses the fabianus account. Thus once the file uploaded it is owned by fabianus. But the magento application runs under the apache user (www-data). And this www-data has not the rights on this uploaded file. 
So what I want is to make it proper, so that once the guy uploaded the file magento may access it. What should I do ?

1) make the guy use the www-data user to connect to the ftp-server, so that the uploaded file will have the correct rights. 

2) make something so that www-data user has the right to use files uploaded by fabianus (don't think that this is proper, what do you think?)

3) create a special ftp-user (like magentoadmin) that may upload the file though the ftp server, but the www-data user has to have the rights to access this uploaded file. 

Perhaps I missunderstand how users have to work in lunux (I am windows guy :-). 

So thanks a lot to anybody who is ready to make the efford to clear this situation !

Regards, 
Fabianus

---

### Post by Brucevdk on 2009-04-18
> **fabianus said:**
> What should I do ?

It would be helpful if you could display the permissions on the directories and files by pasting the output for ls -lR.

Assuming there isn't just some permission issue 'd go with POSIX ACLs (Access Control Lists). If you are using ext3 you'll have to edit /etc/fstab and add acl to the options to enable support for ACLs, so the options should look like:

```

relatime,errors=remount-ro,acl

```

Then you'll have to apply the correct ACLs to the directory the user fabianus uploads the files to. Here's an example (make sure you sudo apt-get install acl first):

```

setfacl -Rm u:www-data:rwx foobar/
setfacl -Rdm u:www-data:rwx foobar/

```

This will recursively (R) modify (m) the ACLs on the directory foobar to give the user (u) www-data read, write and execute permissions (rwx). The d stands for default, which means that www-data will also have rwx to any new file or directory created in foobar.

Here's the result:

```

$ getfacl foobar/
# file: foobar/
# owner: bruce
# group: bruce
user::rwx
user:www-data:rwx
group::r-x
mask::rwx
other::r-x
default:user::rwx
default:user:www-data:rwx
default:group::r-x
default:mask::rwx
default:other::r-x

```

---

