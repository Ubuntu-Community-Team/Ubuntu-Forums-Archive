---
title: "NetHack, Help installing Tactical Amulet Extraction Bot [TAEB]"
date: 2010-03-25
forum: Gaming &amp; Leisure
---

### Post by zeroluck on 2010-03-25
The Tactical Amulet Extraction Bot [TAEB] is a framework/bot that plays NetHack all by itself dealing with some competence against the infinite number of situations and dangers that the Random Number Generator [RNG] throws at it.

And if you have knowledge of Perl 5 and Moose you can also make your own bot using TAEB as a framework.

For more info:

[TAEB's Blog]("http://taeb-blog.sartak.org/")
[TAEB's Web page]("http://taeb.sartak.org/")
[TAEB's Source]("http://github.com/sartak/TAEB")

Ok now my problem. In short, the installation went without any problem, but when I try to run taeb I get a missing module error.

Here are the outputs of the installation and **taeb.**

perl Makefile.PL
[http://pastebin.com/MF5Zt4vQ]("http://pastebin.com/MF5Zt4vQ")

make && sudo make install
[http://pastebin.com/9fHRukJH]("http://pastebin.com/9fHRukJH")

taeb
[http://pastebin.com/4HUXSvZa]("http://pastebin.com/4HUXSvZa")

Theses are the steps I made to install TAEB in a machine running Xubuntu 9.10 with NetHack installed.

Following the instructions in this page: 

[http://github.com/sartak/TAEB/blob/master/README]("http://github.com/sartak/TAEB/blob/master/README")

First, I installed **git** to be able to download TAEB from the repo.

```
sudo apt-get install git-core
```

Then downloaded TAEB.

```
mkdir ~/games
cd ~/games
git clone git://github.com/sartak/TAEB.git
```

as instructed by the README, installed some compilers.

```
sudo apt-get install build-essential
sudo apt-get install libncurses5-dev
```

Now the makefile.

```
perl Makefile.PL
```

Install TAEB

```
make && sudo make install
```

During the installation I simply answered yes to any module to install.

And finlly run taeb

```
taeb
```

I get a error when I try run taeb. Something about a missing module named Moose::Meta::Attribute::Custom::Counter (see taeb output). I searched for this module in  Google and the only relevant result I found was a page:
 
[http://search.cpan.org/~stevan/MooseX-AttributeHelpers-0.04/](http://search.cpan.org/~stevan/MooseX-AttributeHelpers-0.04/) 

that had the module I needed. So I assumed it was just a matter of installing the missing library.

```
sudo apt-get install libmoosex-attributehelpers-perl
taeb

```

And... no luck, it gave me the same error. Maybe I should install some more moose libraries and see if that helps. 

```
sudo apt-get install libmoose-perl
sudo apt-get install libany-moose-perl
sudo apt-get install libmoosex-getopt-perl
sudo apt-get install libmoosex-traits-perl
sudo apt-get install libmouse-perl
sudo apt-get install libmoosex-types-perl
sudo apt-get install libmoosex-types-path-class-perl
```

Nope, the same error again. Well, let's try the configuration file.

```
cd ~/.taeb
bash: cd: /home/romulo/.taeb: No such file or directory
```

So, there was no cofiguration file. The Readme tells me to look at TAEB::Config which actually means to read this file:

**/usr/local/share/perl/5.10.0/TAEB/Config.sm**

Ok found what I need and created the config.yml file:

```
cat ~/.taeb/config.yml
    --- 
    #### Mandatory options #### 
    # What should be controlling TAEB 
    ai: Demo 
    # How TAEB should communicate with NetHack (another option is Telnet) 
    interface: Local 
    # How TAEB should communicate with you! 
    display: Curses 

taeb
```

All this didn't help either. It gave the same error again. So now to make sure it was reading the configuration:

```
taeb --config=~/.taeb/config.yml
```

Same result. 

I don't know what to do now but I really want to make this to work.

Any suggestion?

---

### Post by zeroluck on 2010-03-26
I found the solution here:

[http://github.com/daxim/TAEB/commit/6f857db64216e319ee4ef339342b9c6e3ebb851d](http://github.com/daxim/TAEB/commit/6f857db64216e319ee4ef339342b9c6e3ebb851d)

I short you have to install libmoosex-attributehelpers-perl

```
sudo apt-get install libmoosex-attributehelpers-perl
```

and insert in /usr/local/share/perl/5.10.0/TAEB.pm at line 3

**use MooseX::AttributeHelpers;**

so it should look like this:

```
package TAEB;
use 5.008001;
**use MooseX::AttributeHelpers;**
use TAEB::Util qw/:colors tile_types item_menu/;

use TAEB::OO;

```

You could also download the source already fixed from here:

```
git clone git://github.com/daxim/TAEB.git
```

I hope this will help someone in the future.

---

### Post by oldrocker99 on 2010-03-26
Hmmm...I've played Nethack off and on for about 20 years, and always by myself. What this is sounds a little like Progress Quest;)

:guitar:

---

