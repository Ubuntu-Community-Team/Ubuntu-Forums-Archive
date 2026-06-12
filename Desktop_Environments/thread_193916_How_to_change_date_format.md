---
title: "How to change date format?"
date: 2006-06-10
forum: Desktop Environments
---

### Post by tgcUbuntu on 2006-06-10
I just installed Ubuntu Dapper 6.06. When I run programs that display dates(such as Thunderbird, and Quicken under Wine) I get the date format of dd/mm/yy. I would like to have the format as mm/dd/yy. Is there a way to change this format?

---

### Post by Niloc on 2006-10-02
I have exactly the same problem but in reverse! I want dd/mm/yy and all I can get is mm/dd/yy. There must be some way of changing it....

---

### Post by PigCorpse on 2006-10-02
Go to the regional settings. I wish I can be more detailed, but not home now.

---

### Post by kxs on 2006-11-04
I would also like to know how to change it. Mine is set to "sob lis  4 12:39:16 CET 2006" as I want "2006-11-04 12:39:16"
How to change it?

After 
```
locale -k LC_TIME
```
I get this:
```
abday="nie;pon;wto;&#347;ro;czw;pi&#261;;sob"
day="niedziela;poniedzia&#322;ek;wtorek;&#347;roda;czwartek;pi&#261;tek;sobota"
abmon="sty;lut;mar;kwi;maj;cze;lip;sie;wrz;pa&#378;;lis;gru"
mon="stycze&#324;;luty;marzec;kwiecie&#324;;maj;czerwiec;lipiec;sierpie&#324;;wrzesie&#324;;pa&#378;dziernik;listopad;grudzie&#324;"
am_pm=";"
d_t_fmt="%a %d %b %Y %T %Z"
d_fmt="%Y-%m-%d"
t_fmt="%T"
t_fmt_ampm=""
era=
era_year=""
era_d_fmt=""
alt_digits=
era_d_t_fmt=""
era_t_fmt=""
time-era-num-entries=0
time-era-entries="n"
week-ndays=7
week-1stday=19971130
week-1stweek=0
first_weekday=2
first_workday=1
cal_direction=1
timezone=""
date_fmt="%a %b %e %H:%M:%S %Z %Y"
time-codeset="UTF-8"

```

The second last line:
```
date_fmt="%a %b %e %H:%M:%S %Z %Y"
```
stands for my time format. So, I think thata all I have to do is to find it and change it, but... I`m stuck here ](*,)

---

### Post by Brocco on 2007-04-03
OK, I just figured this out, though the solution's a bit more involved than I like.

I'm an American, and I'm not too provincial to realize that we use a brain-dead date format (%m-%d-%Y).  I'd much rather use (and do as much as I can) the ISO format (%Y-%m-%d).

Here are the steps I took to accomplish this.  Hopefully there's a simpler way:

$ cd /usr/share/i18n/locales
$ sudo cp en_US custom

In the file "custom", I changed the lines:

```
% Appropriate date representation (%x)
%       "%m/%d/%Y"
d_fmt   "<U0025><U006D><U002F><U0025><U0064><U002F><U0025><U0059>"

```
to:
```

% Appropriate date representation (%x)
%       "%Y-%m-%d"
d_fmt   "<U0025><U0059><U002D><U0025><U006D><U002D><U0025><U0064>"

```

$ sudo localedef -f UTF-8 -i custom custom.UTF-8

In /etc/environment, I added:

LC_TIME="custom.UTF-8"

Originally I changed LANG to "custom.UTF-8", which seemed to work fine except my fonts in Firefox got really small!  Weird.

I logged out and logged back in, and then applications such as GnuCash picked up the new date format automatically.

Cheers,
Brocco

---

### Post by gdallosto on 2008-01-07
I am new Linus/Ubuntu user.

How do I set the date/time format to the following:  YYYY MMM dd    HH:mm   
 ( 24 hour format )  

Where can I find the description of the format below:  <U0025><U0059>   ?????

% Appropriate date representation (%x)
%       "%Y-%m-%d"
d_fmt   "<U0025><U0059><U002D><U0025><U006D><U002D><U0025><U0064>"

Thanks.......

---

### Post by willix on 2008-07-20
Brocco

This is the best post I've found on the subject. I'd add for newbies the following:
The date format (i.e. %Y-%m-%d) is explained here [http://au2.php.net/strftime](http://au2.php.net/strftime) 

That string has then to be converted to unicode; the 127 first characters of unicode are the same as ascii and an ascii table can be found here  [http://www.asciitable.com/](http://www.asciitable.com/)

so 
<U0025>=%
<U0059>=Y
<U002D>=-

and so on

I've just installed a new 8.04 version of Ubuntu, and they still haven't got a panel/wiget/screen that does this kind of stuff for you (windows has had it for ages). Shame!

---

