---
title: "how to enable or install curl on linux red hat"
date: 2009-02-16
forum: Fedora/RedHat and derivatives
---

### Post by my_everything78 on 2009-02-16
Hello everybody 

I know that this forum is for Ubuntu , but i thought that you might help me in redhat distribution 

I want to istall curl package for php5 , all i read about is that if you want to install curl you need to recompile the php , the problem is im talking about the company server that im working in , so i cant change any configuration for php .

I dont want to make any mistake in php , so problems wont happen.

So is there a way that i can install this package without recompiling the php..

in ubunto it is alot easier to install this package ... 
but in redhat commands are different . and im ubuntu user ..

so any body can give me a hand :)

Thank you guys for your support.

---

### Post by binbash on 2009-02-16
Did you install the apache or php via packages or compiled yourself?If you compiled them you have to recompile.

---

### Post by my_everything78 on 2009-02-16
Hello binbash

Well to make things clear this server is a dedicated server from planet .
so when we I mean the company bought the server , everything were set up ..
so i didnt do anything , and things were greate .
now there is a need to use curl functions in php , so i need to enable it in the php which is in the server (redhat) , i have no clue how to deal with redhat or how to add a package to php , thats why im afraid from post which says to recompile php with curl package.

so is there any easy way to do that ?
Im really sorry if Im asking too much ..

Thank you for your kindness

---

### Post by binbash on 2009-02-16
Hey my_everything78

You have to recompile the php with '--with-curl=/opt/curl/' (/opt/curl is the dir where is curl)

I STRONGLY suggest sticking to a good howto.AND compile apache, php and curl
(DonT forget to install development packages like curl-devel etc, else you will see errors while compiling)

---

### Post by my_everything78 on 2009-02-16
Hello binbash

First thank you so much for fast responding ..
Second , I guess Im kinda confused ...

is there any documentation that can show me in a simple way step by step what to do from the start..

as I told you im a newbie in Ubunto , regarding redhat I never even istalled it . so my knowledge there is zero..

so is it possible to find such a documentation ...
I dont want to mess things in the server :(

Thank again for you support ..
You so kind

---

### Post by YeOK on 2009-02-16
> **my_everything78 said:**
> Hello everybody 

I know that this forum is for Ubuntu , but i thought that you might help me in redhat distribution 

I want to istall curl package for php5 , all i read about is that if you want to install curl you need to recompile the php , the problem is im talking about the company server that im working in , so i cant change any configuration for php .

I dont want to make any mistake in php , so problems wont happen.

So is there a way that i can install this package without recompiling the php..

in ubunto it is alot easier to install this package ... 
but in redhat commands are different . and im ubuntu user ..

so any body can give me a hand :)

Thank you guys for your support.

What version of Fedora / Red Hat are you using ?

```

cat /etc/redhat-release

```

Edit: Well, anyway. Having to re-compile PHP for curl support was in old versions. just do,

```

# yum install curl curl-devel

```

Then restart your httpd server,

```

# service httpd restart

```

That should sort you out. Also make sure your server is fully updated,
```

# yum update

```

---

