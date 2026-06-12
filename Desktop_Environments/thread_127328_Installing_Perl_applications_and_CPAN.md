---
title: "Installing Perl applications and CPAN"
date: 2006-02-08
forum: Desktop Environments
---

### Post by Mustard on 2006-02-08
I've been trying my hand at compiling a few applications from source, and I've started running into Perl applications that require you to use CPAN to download specific modules.  I've fumbled my way through and ended up with a .cpan directory in my $HOME directory, but I've always had the nagging doubt that they should be installed somewhere else, or that the  modules already exist somewhere else.  Can anyone with experience in installing Perl modules on ubuntu give me some tips as to where my CPAN modules need to be stored and how you would configure CPAN to install them there?

---

### Post by polpak on 2006-02-08
This took me a while to figure out also, but essentially you don't need to get the stuff from CPAN (unless the thing you're trying is very version specific). Ubuntu packages all the cpan modules for you. 

For example if you need to make use of the CPAN module XML::Parser you can just

sudo apt-get install libxml-parser-perl

So the format should be lib(your package name in lower case with - instead of :: )-perl

---

### Post by Mustard on 2006-02-08
Ah ok...I'm discovering these packages as we speak. :)  Thanks.

---

### Post by devnulljp on 2006-02-08
Is there a specific repository that should be enabled for cpan packages? I'm having no luck installing perl modules through the usual method:
sudo perl -MCPAN -e 'install whatever::modulename'
Not having any luck with apt-get either - none of the perl modules I want seem to be available.

---

### Post by nanotube on 2006-02-09
you have to enable the universe repository to get the perl packages. (in synaptic go to Setings>repositories> Add, and check universe.

---

### Post by devnulljp on 2006-03-20
my bad...looks like peerguardian is blocking cpan.

---

### Post by chochem on 2008-02-16
Uhm so how would one go about using such modules? Typin 'perl <name of module>' in the terminal doesn't seem to do the job.....

---

### Post by s3gfault on 2008-02-16
> **chochem said:**
> Uhm so how would one go about using such modules? Typin 'perl <name of module>' in the terminal doesn't seem to do the job.....
they are used in the body of the perl script.

[http://perldoc.perl.org/functions/use.html](http://perldoc.perl.org/functions/use.html)

---

### Post by chochem on 2008-02-16
ah okay so I would really have to find a script and run that  (and if that required any modules, install as explained above, yes? And running perl scripts on ubuntu is simply a matter of typing perl <name of script>?

---

### Post by s3gfault on 2008-02-16
> **chochem said:**
> ah okay so I would really have to find a script and run that  (and if that required any modules, install as explained above, yes? And running perl scripts on ubuntu is simply a matter of typing perl <name of script>?

thats right.  If you aren't a developer then most likely you'll one see these names when you run into these dependencies just like OP did, when you are trying to use a script someone else wrote that requires one.

---

### Post by chochem on 2008-02-16
No developer, no. I was just looking for possible id3 tagging solutions and googled for perl and mp3 and ended up on CPAN :)

Thanks for the clarification.

---

