---
title: "Hardy Error in Package Manager Help."
date: 2008-04-26
forum: Desktop Environments
---

### Post by phillip_style on 2008-04-26
Hello all,
May I start off by saying this is my first post and I am in no way an experienced Linux user.
When it first installed everything was working as should with no issues.
After installing my software etc I log on to see a stop icon in my tray saying: 

"An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.
The error message was:'Error: Opening the cache (E:Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.)'This usually means that your installed packages have unmet dependencies."

Because of the error I cannot run add/remove programs or package manager.

Any advice would be appreciated.
Thanks,
Phil

---

### Post by phillip_style on 2008-04-26
bump

---

### Post by Linja on 2008-04-26
Have you had a look at that /etc/apt/sources.list file? The error is suggesting that it has an incomplete DTD tag on line 1. And how did you install medibuntu? Did you use wget?

---

### Post by phillip_style on 2008-04-26
Linja thank you so so much for your reply.
I have had a look but from what I see I cannot see any issues but as already stated I am not experienced in this field.
Please see below for my sources.list:

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe

---

### Post by phillip_style on 2008-04-26
Just another note I do not know if this will help anymore but when I open Synaptic Package Manager I get the following error: 

E: Type ‘<!DOCTYPE’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.


So I opened the file mentioned which has this:

  <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "DTD/xhtml1-strict.dtd">
                <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
                <head>
                    <title>Medibuntu :: Multimedia, Entertainment &amp; Distractions In Ubuntu</title>
                    <meta http-equiv="Content-Type" content="text/xhtml+xml; charset=utf-8" />
                    <link rel="stylesheet" href="medibuntu.css" type="text/css" />
                </head>
                    <body>
                        <div id="header">
                            <h1><span class="hidden">Medibuntu<br />Multimedia, Entertainment &amp; Distractions In Ubuntu</span></h1>
                        </div>
                        <ul id="menu"><li><a href="index.php">Presentation</a></li>
                        <li><a href="http://help.ubuntu.com/community/Medibuntu">Repository Howto</a></li>
                        <li><a href="packages.php">Packages</a></li>
                        <li><a href="contact.php">Contact us</a></li>
                                 </ul>
        <div id="page">
              <h2>Presentation</h2>
                                <p>
                                    <strong>
                                        Medibuntu (Multimedia, Entertainment &amp; Distractions In Ubuntu) is a repository of packages that cannot be included into the Ubuntu distribution for legal reasons (copyright, license, patent, etc).
                                    </strong>
                                </p>
                                <p>
                                    Medibuntu is a packaging project dedicated to distributing software that cannot be included in Ubuntu for various reasons, related to geographical variations in legislation regarding intellectual property, security and other issues:
                                </p>
                                <ul>
                                    <li>patentability of software, algorithms, formats and other abstract creation</li>
                                    <li>legal restrictions on freedom of speech or communication</li>
                                    <li>restrictions on the use of certain types of technical solution, such as cryptography</li>
                                    <li>legal restrictions on imports of software technology, requiring for example specific permissions</li>
                                    <li>etc.</li>
                                </ul>
                                <p>
                                    A lot of excellent <a href="http://www.fsf.org/licensing/essays/free-sw.html">free software</a> and non-free software is affected by such restriction somewhere in the world, thus preventing its inclusion into Ubuntu that, for economy and simplicity, are generally identical for all countries.
                                </p>
                                <p>
                                    We refuse to resign ourselves to abandoning software that may be legally useful somewhere, and we have chosen to provide it with professional quality packaging, easily usable within the context of Ubuntu.<br />
                                    This repository provides packages for Ubuntu distribution.
                                </p>
                                <p>
                                    It is your legal responsibility to make sure that the software you are installing can be legally used in your country and for your intended purpose.
                                </p>
                                        </div>
          <div id="paypal"><form action="https://www.paypal.com/cgi-bin/webscr" method="post">
<p>
<input type="hidden" name="cmd" value="_xclick" />
<input type="hidden" name="business" value="maxenced@gmail.com" />
<input type="hidden" name="item_name" value="Medibuntu" />
<input type="hidden" name="no_shipping" value="0" />
<input type="hidden" name="no_note" value="1" />
<input type="hidden" name="currency_code" value="EUR" />
<input type="hidden" name="tax" value="0" />
<input type="hidden" name="bn" value="PP-DonationsBF" />
<input type="image" src="https://www.paypal.com/en_US/i/btn/x-click-but04.gif" name="submit" alt="Effectuez vos paiements via PayPal : une solution rapide, gratuite et sécurisée" />
<img alt="" src="https://www.paypal.com/en_US/i/scr/pixel.gif" width="1" height="1" />
</p>
</form>
          </div>
                        <div id="footer">:: designed by <a href="http://www.most-enchained.com">_Enchained</a> - logo by <a href="http://www.racoon97.net">racoon97</a> - Domain by <a href="http://flosoft.biz">Flosoft</a>  - Managed by <a href="http://www.dunnewind.net">Sp4rKy</a> ::          </div>
<!-- phpmyvisites -->
<a href="http://www.phpmyvisites.us/" title="phpMyVisites | Open source web analytics"
onclick="window.open(this.href);return(false);"><script type="text/javascript">
<!--
var a_vars = Array();
var pagename='';

var phpmyvisitesSite = 2;
var phpmyvisitesURL = "http://stats.dunnewind.net/phpmyvisites.php";
//-->
</script>
<script language="javascript" src="http://stats.dunnewind.net/phpmyvisites.js" type="text/javascript"></script>
<object><noscript><p>phpMyVisites | Open source web analytics
<img src="http://stats.dunnewind.net/phpmyvisites.php" alt="Statistics" style="border:0" />
</p></noscript></object></a>
<!-- /phpmyvisites --> 
    </body>
                </html>


Any help would mean a lot!
Thanks,
Phil

---

### Post by Linja on 2008-04-26
Oops, now that I read your previous post again, I see that Medibuntu is in a separate file inside /etc/apt/sources.list.d. These should be the contents, nothing more:

## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

Edit: I missed your last post. Well, if those are the contents of your medibuntu file, it's no wonder you are having issues. Make a backup, then replace all those lines in the original file with the proper four lines. You may need to run sudo apt-get update from the command line after that to get things back into working order.

---

### Post by phillip_style on 2008-04-26
> **Linja said:**
> Oops, now that I read your previous post again, I see that Medibuntu is in a separate file inside /etc/apt/sources.list.d. These should be the contents, nothing more:

## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

THANK YOU THANK YOU THANK YOU THANK YOU.
I hope you have a brilliant day my friend worked like a charm!

---

### Post by tfkroko on 2008-07-05
How does one "look at that /etc/apt/sources.list file"?

A frustrated new user who only wanted to look at pdf's but can't. tfkroko

---

