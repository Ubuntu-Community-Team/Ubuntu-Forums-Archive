---
title: "Synaptic Error"
date: 2009-04-01
forum: General Help
---

### Post by i_am_skittles on 2009-04-01
Hello Ubuntu community! So, I have had ubuntu for around 4 days or so, and I am still VERY new at all this, so please bear with me. So anyways, I had been having some trouble using the synaptic package manager, when I try to open it up, I get this error message:

E: Line 1 too long in source list /etc/apt/sources.list.d/medibuntu.list.
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report

Um, so could someone out there pretty please tell me what's going on? And what is the repository dialog?

Many, many thanks in advance!!
Oh, btw I'm using Ubuntu 8.10

---

### Post by Cheesehead on 2009-04-01
Please open the file '/etc/apt/sources.list.d/medibuntu.list' in gedit or mousepad or another text editor, and paste the contents of the file in your reply. That way, we can see the problem.

---

### Post by i_am_skittles on 2009-04-01
Um, okay thanks, I am really new at this, so just tell me what you need and I'll try to get for ya...So, I found the file, but I don't know if it is the right one, if not, I'll look some more, but here's what I got:

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"><html xmlns="http://www.w3.org/1999/xhtml"><head><title>Mediacom Search Guide</title><meta http-equiv="content-type" content="text/html; charset=UTF-8"><meta http-equiv="Pragma" content="no-cache"><meta http-equiv="Expires" content="-1"><meta name="robots" content="nofollow"><meta http-equiv="X-UA-Compatible" content="IE=7" /><link title="Mediacom" rel="search" type="application/opensearchdescription+xml" href="/add_search.php"/><link rel="shortcut icon" href="favicon.ico"><link rel="stylesheet" type="text/css" media="screen" href="./css/core_nxd.css" /><!--[if IE]><link rel="stylesheet" type="text/css" media="screen" href="./css/ie_core_nxd.css" /><![endif]--><script type="text/javascript">var phrase_orig='wget';var phrase_one='Type Your Search Here';var phrase_two='Please, Type Your Search Here';</script><script src="./js/common_jscript.js" type="text/javascript"></script><script src="./js/detectBrowser.js" type="text/javascript"></script></head>    <style type="text/css">
        #top { margin: 3px 10px; font-size: 13pt; }
        #top a {
            font-size: 11pt;
        }
        .bottom_form {
            display: none;
        }
        #suggestion_table {
            padding: 40px 0px;
        }
        #rss_listings {
            margin: 10px 5px;
        }
    </style><body>    <div id="whatsthis" style="left: 0px; display: none;">
        <div class="whatsthisbody">
            <a class="close" href="#" onclick="toggleDetails(event);return false;"><img src="./img/close_button.jpg"/></a>
            <div class="wttitle">Why am I here?</div>
            <p>The Mediacom redirection service has been enabled to provide helpful searches from web address errors. You entered an unknown name that the Mediacom service used to present site suggestions which you may find useful. Clicking any of these suggestions provides you with Yahoo! search results, which may include relevant sponsored links.</p>
            <div class="wttitle">Can I opt out of this service?</div><p>If this service is not right for you, please visit your <a href="prefs.php">Preferences</a> page to opt out. At any point in time, you can opt back in to the service by visiting your <a href="prefs.php">Preferences</a> page.</p>
            <div class="wttitle">What if I still have questions?</div>
            <p>If you have other questions about this service, please visit our <a href="faq.php">Faq</a></p>
        </div>
        <div class="whatsthisbottom">&nbsp;</div>
    </div><div class="upper_menu"><span class="home"><a href="http://www.mediacomcable.com">Home</a> | </span><span class="home"><a target="_self" href="http://www.mediacomcc.com/vip_redirect.php">Special Offers</a> | </span><span class="home"><a target="_self" href="http://www.mediacomcc.com/cable_tv.html">Cable TV</a> | </span><span class="home"><a target="_self" href="http://www.mediacomcc.com/internet.html">Internet</a> | </span><span class="home"><a target="_self" href="http://www.mediacomcc.com/phone.html">Phone</a> | </span><span class="home"><a target="_self" href="http://www.mediacomcc.com/business_services.html">Business Services</a> | </span><span class="home"><a target="_self" href="http://www.mediacomcc.com/customer_support.html">Customer Support</a> | </span><span class="home"><a class="last" target="_self" href="http://www.mediacomcc.com/about_us.html">About Us</a></span><span class="why"><a href="#" class="whyamihere" onclick="toggleDetails(event);return false;" title="More Details">Why Am I Here?</a></span></div><div class='top_form'><center>
    <form action="index.php" name="headersearchform" id="headersearchform" class="searchForm">
        <table border="0" cellpadding="0" cellspacing="0">
            <tr valign="top">
                <td class="logo"><a href="http://www.mediacomcc.com"><img src="./img/logo_top_home.gif" alt="logo"/></a></td>
                            <td class="centerCell">
                <div class="inputHolder"><input type="text" size="50" id="queryBoxTop" class="queryBox" name="search" value="wget"/></div>
            </td>
            <td class="centerCell">
                <input type="submit" name="submit" value="Search" class="button" size="50px" id="buttonheadersearchform" style=""/>
                <div id="suggestionBox" style="display: none;height: 0px;"></div>
            </td>
            <td class="centerCell">
                <span id="buttonRightheadersearchform" style="margin-left:0em;"><img src="./img/search_box_button_right.jpg" class="button_right"/></span>
            </td>
            <td class="centerCell">
                <a href="http://www.yahoo.com" title="Yahoo!"><img src="img/pb_yahoo.gif" alt="Yahoo!" style="" class="yahoo_img"/></a>
            </td>
            </tr>
        </table>
        
        
    </form>
</center></div><div class="welcome">Mediacom Search Guide</div><center><table id="suggestion_table" cellpadding="0" cellspacing="0">                    <tr><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Travel">Travel</a></td><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Financial+Planning">Financial Planning</a></td><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=E+Commerce">E Commerce</a></td></tr>
                    <tr><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Lifestyle">Lifestyle</a></td><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Real+Estate">Real Estate</a></td><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Insurance">Insurance</a></td></tr>
                    <tr><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Business">Business</a></td><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Legal+Help">Legal Help</a></td><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Personal+Finance">Personal Finance</a></td></tr>
                    <tr><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Computers">Computers</a></td><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Health+Care">Health Care</a></td><td><a rel='nofollow' onmouseover='return true;'  href="index.php?search=Shopping">Shopping</a></td></tr>
</table></center><div class='bottom_form'><center>
    <form action="index.php" name="searchform" id="searchform" class="searchForm">
        <table border="0" cellpadding="0" cellspacing="0">
            <tr valign="top">
                <td class="logo"><a href="http://www.mediacomcc.com"><img src="./img/logo_top_home.gif" alt="logo" style="display: none;"/></a></td>
                            <td class="centerCell">
                <div class="inputHolder"><input type="text" size="50" id="queryBoxBottom" class="queryBox" name="search" value="wget"/></div>
            </td>
            <td class="centerCell">
                <input type="submit" name="submit" value="Search" class="button" size="50px" id="buttonsearchform" style=""/>
                <div id="suggestionBox" style="display: none;height: 0px;"></div>
            </td>
            <td class="centerCell">
                <span id="buttonRightsearchform" style="margin-left:0em;"><img src="./img/search_box_button_right.jpg" class="button_right"/></span>
            </td>
            <td class="centerCell">
                <a href="http://www.yahoo.com" title="Yahoo!"><img src="img/pb_yahoo.gif" alt="Yahoo!" style="" class="yahoo_img"/></a>
            </td>
            </tr>
        </table>
        

Thanks for your patience

---

### Post by i_am_skittles on 2009-04-01
This is probably a dumb question, but this seems like a website...is that what it is supposed to be?

---

### Post by plucky on 2009-04-02
> **i_am_skittles said:**
> This is probably a dumb question, but this seems like a website...is that what it is supposed to be?

It is supposed to be a repository.
This is what my file contains ```
## Medibuntu - Ubuntu 8.10 "intrepid ibex"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ intrepid free non-free
# deb-src http://packages.medibuntu.org/ intrepid free non-free

```

See this [link](https://help.ubuntu.com/community/Medibuntu) for adding the Medibuntu repository. I would delete that file first.

From a terminal
```
cd /etc/apt/sources.list.d/
ls
sudo rm medibuntu.list
```

Ths ls command is to make sure you are in the correct directory.You need to use sudo to remove the file as it is a system file.



Good Luck

---

