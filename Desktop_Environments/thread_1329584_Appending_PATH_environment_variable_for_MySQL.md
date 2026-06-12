---
title: "Appending PATH environment variable for MySQL"
date: 2009-11-17
forum: Desktop Environments
---

### Post by Bupkus on 2009-11-17
I'm in the process of installing MySQL for testing and skipped the step to change the environment variable PATH for the shell to locate mysqld.
Here is a paste from the terminal:
[FONT="Fixedsys"]
root@mark-desktop-ubuntu:/usr/local/mysql-5.1.40-linux-i686-icc-glibc23# pwd
/usr/local/mysql-5.1.40-linux-i686-icc-glibc23

root@mark-desktop-ubuntu:/usr/local/mysql-5.1.40-linux-i686-icc-glibc23# scripts/mysql_install_db --user=mysql

FATAL ERROR: Could not find mysqld

The following directories were searched:

    /usr/libexec
    /usr/sbin
    /usr/bin[/FONT]

[B]As you can see the folder I need searched is not listed >> /usr/local/mysql-5.1.40-linux-i686-icc-glibc23/bin
[/B]
Inside /etc is bash_completion with the following entry:

_root_command()
{
	PATH=$PATH:/sbin:/usr/sbin:/usr/local/sbin _command $1 $2 $3
}

I really don't want to modify this line as I don't trust the "_command $1 $2 $3" phrase for what it does. 

What change is needed and how is it performed?

---

