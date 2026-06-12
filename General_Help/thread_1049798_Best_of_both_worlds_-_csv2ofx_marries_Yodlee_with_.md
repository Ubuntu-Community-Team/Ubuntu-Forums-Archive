---
title: "Best of both worlds - csv2ofx marries Yodlee with GnuCash"
date: 2009-01-24
forum: General Help
---

### Post by MountainX on 2009-01-24
I'm starting to like GnuCash. Yodlee is great too. I'm a new user of both (started at beginning of this year), but I am already hooked, especially on Yodlee. Using these two apps together has allowed me to finally stop using MS Money (and that allowed me to finally stop using MS Windows for personal stuff.)

The key to upgrading my personal finance software was a free utility called csv2ofx. Without it, there is no way to get Yodlee data into GnuCash (or any other PFM I know of).

GnuCash (or similar PFM) is required because, as great as Yodlee is at automatically downloading all your banking transactions, there are several things Yodlee cannot do. For example, I need to generate a report of all my account balances as of year end. I cannot do my taxes without this. 

There are other common financial functions (reporting, budgeting, electronic payments via check, etc.) that people need and that are currently best done in apps like GnuCash.

Yodlee does allow you to export all transactions into a CSV file. But to get your data into the common personal financial management apps such as GnuCash, it needs to be in OFX format.

Well, there is now a way to convert Yodlee CSV data into OFX!

csv2ofx is free and open source. Get it here:
[http://github.com/mulicheng/csv2ofx/](http://github.com/mulicheng/csv2ofx/)

By using csv2ofx you can continue to reap all the benefits of Yodlee and you can also take advantage of more advanced features available in GnuCash, etc.

(An earlier forum post about it can be found here: [http://ubuntuforums.org/showpost.php?p=6594351&postcount=10](http://ubuntuforums.org/showpost.php?p=6594351&postcount=10))

I use csv2ofx to import my Yodlee data into GnuCash where I can do further analysis or processing. I enjoy the best of Yodlee and the best of GnuCash.

Without csv2ofx, I would have to give up on Yodlee and GnuCash and go back to MS Money. I have to be able to get the account balances required for tax accounting. MS Money allowed me to do this easily. GnuCash can do it, but its online transaction downloading is too much of a pain for me. So GnuCash by itself is out of the question. But blending Yodlee and GnuCash is wonderful and I am glad I don't have to go back to MS Money.

(However, csv2ofx will also let you transfer Yodlee data to MS Money or Quicken and maybe even MoneyDance, KMyMoney, and others too.)

---

### Post by MountainX on 2009-02-02
UPDATE: QIF supported added too now.

---

### Post by BuddyLee13 on 2009-07-31
Hi - I'm trying to run this on Jaunty and getting the error below.  I'm not all that familiar with python but from making some feeble attempts to rectify it (commenting out the line with the attribute), got further until I ran into another error when attempting to export.  

I believe I have all the correct dependencies installed and have exhausted all attempts to try and figure this out on my own.

Does anyone have this working under Jaunty and/or have any ideas on what to check next?

Thanks!

```
Traceback (most recent call last):
  File "/usr/local/bin/csv2ofx", line 14, in <module>
    a=csv2ofx.csv2ofx()
  File "/usr/local/lib/python2.6/dist-packages/csv2ofx/__init__.py", line 25, in __init__
    wx.App.__init__(self,redirect=False)
  File "/usr/lib/python2.6/dist-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7700, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.6/dist-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7352, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/local/lib/python2.6/dist-packages/csv2ofx/__init__.py", line 46, in OnInit
    self.grid.EnableEditing(False)
AttributeError: 'NoneType' object has no attribute 'EnableEditing'
```

---

### Post by MountainX on 2009-07-31
I am not familiar with python either, but I will look into this and if I can understand the error, I'll reply back with some help. Give me a few days...

You can also contact the developer via the link at GitHub (where you can download the code).

Cheers

---

### Post by MountainX on 2009-09-09
> **BuddyLee13 said:**
> Hi - I'm trying to run this on Jaunty and getting the error below.  I'm not all that familiar with python but from making some feeble attempts to rectify it (commenting out the line with the attribute), got further until I ran into another error when attempting to export.  

I believe I have all the correct dependencies installed and have exhausted all attempts to try and figure this out on my own.

Does anyone have this working under Jaunty and/or have any ideas on what to check next?

Thanks!

```
Traceback (most recent call last):
  File "/usr/local/bin/csv2ofx", line 14, in <module>
    a=csv2ofx.csv2ofx()
  File "/usr/local/lib/python2.6/dist-packages/csv2ofx/__init__.py", line 25, in __init__
    wx.App.__init__(self,redirect=False)
  File "/usr/lib/python2.6/dist-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7700, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.6/dist-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7352, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/local/lib/python2.6/dist-packages/csv2ofx/__init__.py", line 46, in OnInit
    self.grid.EnableEditing(False)
AttributeError: 'NoneType' object has no attribute 'EnableEditing'
```

I just downloaded and installed csv2ofx on a clean Jaunty installation. I had no issues like what you saw. I installed python-wxgtk2.8 (2.8.9.1-0ubuntu6) using Synaptic Package Manager. My only guess is that your wxGTK package may not be correct. I followed the steps in the README (which is basically to run "sudo python setup.py install").

The installation when fine and the program runs with no errors. 

However, I did have to do some extra steps to get the files to convert correctly. First, I copied <install_directory>/csv2ofx/src/csv2ofx/mappings.py to /home/MY_USER/csv2ofx_custom.py

I also had to edit the csv2ofx_custom.py file to remove the mapping for Transaction ID (which is no longer in the Yodlee data). See [http://github.com/mulicheng/csv2ofx/issues#issue/1](http://github.com/mulicheng/csv2ofx/issues#issue/1)

Finally, I open the Yodlee CSV file in Open Office and then save again as CSV. (This changes the way the dates are written).

Hopefully, all these extra steps will no longer be required on the next update of csv2ofx.

---

### Post by BuddyLee13 on 2009-09-10
Thanks.  Sorry for not posting back but I ended-up rolling my own and playing around with other direct ofx and screen-scraper solutions in an effort to automate even more than MS Money.  Still not 100% there but I have something working for Yodlee.  Still, I might give this another shot based on your findings just to see.

Thanks again!

---

### Post by MountainX on 2009-09-10
> **BuddyLee13 said:**
>  I ended-up rolling my own and playing around with other direct ofx and screen-scraper solutions in an effort to automate even more than MS Money.  Still not 100% there but I have something working for Yodlee.

Can you say more about what you have working? Is it code you can share?

---

### Post by MountainX on 2009-09-10
I'm copying a post from another thread to this thread for reference.

> **bradhaack said:**
> I think that's a great idea (yodlee -> gnucash).  

OK, we have now set up a project for [csv2ofx]("http://github.com/mulicheng/csv2ofx/tree/master") at github.

This is a python app (tested on Ubuntu 8.04, 9.04) that will convert the Yodlee CSV format to OFX. GnuCash can read the OFX file. 

This means you can use Yodlee to aggregate all your accounts and handle all the electronic downloads. Yodlee updates the accounts automatically and it handles far more banks than any other personal financial management software I have used.

With Yodlee you can download a CSV file of all your transactions (for any period of time, from a week to the entire history in Yodlee).

Then you can use csv2ofx to read all those transactions into GnuCash. GnuCash gives you the reporting and budgeting capabilities that Yodlee doesn't. 

The link for csv2ofx is here: [http://github.com/mulicheng/csv2ofx/tree/master](http://github.com/mulicheng/csv2ofx/tree/master)

The easiest way to get csv2ofx is to just download the zip or tar archive from github. Then check out the [wiki]("http://wiki.github.com/mulicheng/csv2ofx") for installation tips. (Due to some bugs, you really need to read the short wiki page to get things to work.)

You can install the package on your system like this:
 (Assuming Ubuntu, run this from /home/your-user/csv2ofx)
 
 ```
sudo python setup.py install
```If you do this, you should get the csv2ofx script installed somewhere in your path and be able to type:
 
 ```
csv2ofx
```from any directory.

**A note on mappings**. The mappings.py file is extremely flexible. Currently it is optimized for Yodlee's CSV format.

**One final note on dependencies:**

The GUI is programmed with wxPython. On Ubuntu 8.04 wxPython was known as wxGTK. In Ubuntu 9.04, I found it in Synaptic as python-wxgtk2.8.

Some distributions name the package wxPython and some wxGTK. Either way, you may need to use apt (or Synaptic) to install the package if it isn't on your system. There are no other dependencies (as far as I know).

**OPTIONAL**: Another way to get the project is to use "git". The "git clone" link (which creates a local project for you) is available at the link above. But I'll list it here too:
 ```
git clone git://github.com/mulicheng/csv2ofx.git
```If you don't use git yet, on Ubuntu, you can simply add it via Synaptic Package Manager. Then paste the git clone line from above in a terminal.
 
 If you are not familiar with git, you can [download an archive]("http://github.com/mulicheng/csv2ofx/") of the project. If you use git however, and the developer(s) make a change, you'll easily be able to update (just type "git pull" in a terminal from the csv2ofx directory).
 
 After you retrieve the files, you can run the program directly from the source files:
 
 ./csv2ofx

---

### Post by BuddyLee13 on 2009-09-10
> **MountainX said:**
> Can you say more about what you have working? Is it code you can share?

It's been a month+ since I've done anything with it so I'm kind of foggy on the details.  Also, I'm a software developer by trade so I'm ashamed to say that I was really just doing some quick and dirty coding to try and get something working straight away and it's not very reusable at this point, especially since what I have is in a variety of languages I don't use all that often (perl, which I've some exposure to, and python and ruby, neither of which I'd done anything with prior to this)

So to what I did so far...

I had found another example of downloading the Yodlee csv file and creating an OFX file out of it.  I took that and modified it for my own use based on account name mappings, etc.

Beyond Yodlee, I got it in my head that it would be nice not to have to rely on Yodlee itself so I was tinkering with some OFX download scripts I found in combination with some of the GnuCash/aqbanking info that's out there.  I found, however, that support for many of my financial institutions is lacking, requires a setup fee, or is just plain broken.  I therefore gave up on that approach and switched gears to...

...some ruby web automation/scraping.  I have this working with a handful of the institutions I have accounts with and when I get back to it, this is probably the approach I'll go with.  In the long run, it's likely to need continual tweaking to keep up to date with changing UI's, but 1) I prefer the benefits of having a true ofx file vs the pseudo ofx generated from Yodlee's csv and 2) even Yodlee can't get to every account I can manually download from.

Because I was/am just trying GnuCash out for now, what I ended up spending more time on was some perl scripts to cleanup the csv files exported out of MS Money so that I can import them into GnuCash.  I'm still not 100% satisfied with the results, but I haven't had time to work on any of this in the last couple of weeks.

Once I've had time to get back into it and straighten some things out, I'd be more than happy to share.  Until then, if anyone has any specifics they want me to get into or want a copy of the very ugly current version of any of this, let me know.

---

### Post by MountainX on 2009-09-10
Speaking of Microsoft Money, I just put up a mapping file for csv2ofx that handles MS Money data pretty well. Here's the link:

[http://wiki.github.com/mulicheng/csv2ofx/microsoft-money-mapping-file](http://wiki.github.com/mulicheng/csv2ofx/microsoft-money-mapping-file)

---

### Post by BuddyLee13 on 2009-09-11
> **MountainX said:**
> Speaking of Microsoft Money, I just put up a mapping file for csv2ofx that handles MS Money data pretty well. Here's the link:

[http://wiki.github.com/mulicheng/csv2ofx/microsoft-money-mapping-file](http://wiki.github.com/mulicheng/csv2ofx/microsoft-money-mapping-file)

Interesting!  I looked at it quickly and recalled that I exported qif files from Money and was running my perl scripts against those.  I'll have to try the csv method, maybe it's a better approach for me.  

One of the things I was doing with the qif files was checking the transaction amount and category to determine if something with a positive balance was really a refunded expense (and vise versa), as well as playing around with account names and memos for old accounts that are either closed or were assumed by other banks (I've unfortunately had 2 banks go belly-up and get absorbed into other institutions, one where I already had accounts which adds a nice layer of complication and confusion!)

---

### Post by gavinlamont on 2010-12-28
Am using Lucid; Python 2.6 & had to have python-wxgtk2.8 to dodge <AttributeError: 'NoneType' object has no attribute 'EnableEditing> message.

---

### Post by MountainX on 2010-12-28
> **gavinlamont said:**
> Am using Lucid; Python 2.6 & had to have python-wxgtk2.8 to dodge <AttributeError: 'NoneType' object has no attribute 'EnableEditing> message.

Sorry, but I have no idea.

---

### Post by MountainX on 2010-12-28
For completeness of this thread, here is my csv2ofx_custom.py that handles the current Yodlee format (i.e., without a transaction ID).

---

### Post by MountainX on 2011-01-01
This isn't elegant, but it got the job done. If you don't have a better way to import a year's worth of American Express credit card transactions into GnuCash, you can use this example.

Go to [https://online.americanexpress.com/myca/acctsumm/us/](https://online.americanexpress.com/myca/acctsumm/us/)
select the card account (e.g., Blue)
select online statement link
set time period: Jan 1 to Dec 31
click download link
The "Download Transaction Activity" modal dialog pops up:
(options: PDF, XLS OR CSV options)
NOTE: choosing the second tier of options which includes the needed formats (Quicken, MS Money, etc.) will prevent you from being able to download a full year!
choose XLS format
check to include additional transaction details (including merchant address, DBA, etc.)
click the "continue" button
save file

Open the XLS file in Open Office Calc and save it as CSV format, then close.
Open the just saved CSV file in Open Office Calc, import starting from row7, and save it as CSV format, overwriting the existing file.

Verify that the saved file includes a header row. The header is expected to be:

"Date","Foreign Spend","Description","Amount","Extended Details","Doing Business As","Parent Company","Street Address","City, State Zip","Reference","Category","Tags"

Verify that you are using the csv2ofx_custom.py that supports Amex CSV format. 
The last line of the file should look similar to this:
all_mappings = {'Amex CSV':amexCsv, 'Yodlee':yodlee, 'PayPal':paypal, 'Credit Union':cu, 'UBS':ubs, 'MS Money Report (CSV)':msmoneyrep }

If you have more than one Amex credit card, edit the ~/csv2ofx_custom.py as required:
--> Your Amex account name is hard coded into the file! It should match your account name in GnuCash

For completeness, here's the code:
```
def amex_toOFXDate(date):
    return datetime.strptime(date,'%m/%d/%Y').strftime('%Y%m%d')        


def amexCsv_memo(row,grid):
    ext=fromCSVCol(row,grid,'Extended Details')# sometimes None
    ctg=fromCSVCol(row,grid,'Category')# sometimes None
    dba=fromCSVCol(row,grid,'Doing Business As')# sometimes None
    prt=fromCSVCol(row,grid,'Parent Company')# sometimes None
    adr=fromCSVCol(row,grid,'Street Address')# sometimes None
    cit=fromCSVCol(row,grid,'City, State Zip')# sometimes None
    if (len(ext) == 0): ext = ' '
    if (len(ctg) == 0): ext = ' '
    if (len(dba) == 0): ext = ' '
    if (len(prt) == 0): ext = ' '
    if (len(adr) == 0): ext = ' '
    if (len(cit) == 0): ext = ' '    
    return "%s; %s %s %s %s %s" % ( ext, ctg, dba, prt, adr, cit)  

#American Express Credit Card CSV download format
amexCsv = {
    #only OFX export format is working...
    'OFX':{
        'skip':lambda row,grid: False,
        'BANKID':lambda row,grid: 'American Express',
        'ACCTID':lambda row,grid: 'YOUR AMEX ACCOUNT--name should agree with GnuCash account name',
        'DTPOSTED':lambda row,grid: amex_toOFXDate(fromCSVCol(row,grid,'Date')),
        'TRNAMT':lambda row,grid: fromCSVCol(row,grid,'Amount'),
        'FITID':lambda row,grid: fromCSVCol(row,grid,'Reference'),
        'PAYEE':lambda row,grid: fromCSVCol(row,grid,'Description'),
        'MEMO':lambda row,grid: amexCsv_memo(row,grid),
        'CURDEF':lambda row,grid: 'USD',#TODO: fix this when I have an example of foreign spending
        'CHECKNUM':lambda row,grid: fromCSVCol(row,grid,'Reference')
    }
    #QIF has not been created yet...
}

all_mappings = {'Amex CSV':amexCsv, 'Yodlee':yodlee, 'PayPal':paypal, 'Credit Union':cu, 'UBS':ubs, 'MS Money Report (CSV)':msmoneyrep }
```

Open csv2ofx from a terminal:
~/csv2ofx$ csv2ofx

import the saved Amex CSV file
export using Amex CSV format to OFX

import into GnuCash using OFX

unfortunately, the sign of each transaction is incorrect. Debits are imported as credits. For now, I simply inserted a minus in from of each amount in GnuCash and it easily moves the amounts to the correct column. Next time I'll edit the python code to fix this. If someone else wants to do it before I do, please post your result here or at [https://github.com/mulicheng/csv2ofx](https://github.com/mulicheng/csv2ofx)

---

