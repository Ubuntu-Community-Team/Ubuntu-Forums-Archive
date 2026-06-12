---
title: "Run Perl Script at startup"
date: 2009-04-08
forum: General Help
---

### Post by scott29 on 2009-04-08
Hi,

I have a Perl script that is used to kick off a daemon process that keeps my Dynamic DNS service updated with my IP address.

Currently I have to run the following every time I reboot my machine:

sudo perl /home/user/dnsexit/ipUpdate.pl

I have no experience with shell scripting or anything, and I've tried everything I can find in Google to no avail.

Can somebody tell me how I can accomplish having this Perl script executed at bootup?  It seems the best route is to write a shell script and put it in init.d along with a symbolic link or something, but that's just one of the long list of things I've failed on.

Many Thanks!
-scott29

---

### Post by trwww on 2009-04-08
This seems to have the instructions you need:

[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

Also check out apps like ddclient and simiar. They install with this already set up for you.

---

### Post by scott29 on 2009-04-09
ddclient does not work with DNSExit, which is who I use.  It would be nice if it did though.  And I have not heard of the other program you mentioned, and when googling it I couldn't find anything.

The link you gave me is something I've seen, but I still have the overall problem of how to write the shell script.  I know there is more to it then simply putting the command in the there.  I guess I need an example of a shell script that calls a Perl Script.  Any examples out there?  If I had an example I can probably take it from there.

I know I need more in the file than:  sudo perl /home/user/dnsexit/ipUpdate.pl

Thanks
scott29

---

### Post by unutbu on 2009-04-09
The old way is to edit /etc/rc.local
Put 
```

perl /home/user/dnsexit/ipUpdate.pl
```

at the end of the file, but before the line that reads "exit 0".

Ubuntu is migrating to the "upstart" system. Although editing /etc/rc.local works,
the new upstart way (which should also work and be more compatible with future releases of Ubuntu) is to create a file called /etc/event.d/myjobs in which you put 
```

start on runlevel 2
exec perl /home/user/dnsexit/ipUpdate.pl
```
(You can change the filename "myjobs" to anything you like.)

---

### Post by KeyserSoze93 on 2009-04-09
There may be more fancy ways to do it, such as setting it up as a service etc., but I would simply call up /etc/rc.local in a root text editor, and before the line "exit 0" (which is absolutely essential), add the command to call your script, followed (also mission critically) by an "&" (which the program into the background so the system can keep booting.

Sorry, I just realised "unutbu" said this also.

---

### Post by scott29 on 2009-04-09
Using the upstart method worked.  Thank you so much!!

---

### Post by scott29 on 2009-04-09
Just one follow up question.  If there are other scripts and/or commands that I would like to execute at startup in the future, should I just add them to the 'myjobs' file, or should I create separate files in the /etc/event.d directory for each script/command?

Thanks!

---

### Post by unutbu on 2009-04-09
You could do it either way. 
I think if there is no logical connection between the two jobs, I would make separate /etc/event.d/XYZ files for each, but that's just me.

I only know the basics of how to use upstart. For more information on upstart, see [http://screwyouenterpriseedition.blogspot.com/2008/07/upstart-050trunk-job-definitions.html](http://screwyouenterpriseedition.blogspot.com/2008/07/upstart-050trunk-job-definitions.html) and [http://www.linux.com/feature/125977](http://www.linux.com/feature/125977).

---

### Post by scott29 on 2009-05-05
This doesn't work with an upgrade to 9.04.  Any idea what the issue may be?  

I'm not sure if it is related, but after startup my Terminal does not work since the upgrade.  There is a fix for that but it requires a mount after each startup.

---

### Post by unutbu on 2009-05-05
Does ```
perl /home/user/dnsexit/ipUpdate.pl
```
still work from the terminal?

If so, how about try making a new upstart script called

/etc/event.d/mytest
```

start on runlevel 2
exec echo "mytest ran on " $(date) > /tmp/mytest.out
```

Then reboot and see if /tmp/mytest.out is created.

---

### Post by scott29 on 2009-05-06
> **unutbu said:**
> Does ```
perl /home/user/dnsexit/ipUpdate.pl
```
still work from the terminal?

If so, how about try making a new upstart script called

/etc/event.d/mytest
```

start on runlevel 2
exec echo "mytest ran on " $(date) > /tmp/mytest.out
```

Then reboot and see if /tmp/mytest.out is created.

The test worked, so now I have no idea why the perl script doesn't start up.  It is one thing in a long list of things that are broken after upgrading to 9.4.  It was a huge mistake upgrading...

---

### Post by unutbu on 2009-05-06
I have a feeling the /home/user/dnsexit/ipUpdate.pl script is actually being executed at boot time, but for some reason is aborting prematurely or for some other reason failing to perform as expected. Does running it from the terminal after boot yield any clues? (i.e. error messages?)

I'm sorry to hear the upgrade has not gone smoothly.

This may not help you right now, but for the future, you might want to keep your personal data in a separate partition. Then it becomes very easy to reinstall the operating system without destroying the data. (See [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving))

Also, if you have the hard disk space, you could keep an extra 20GB partition around, so when it comes time to upgrade to a new OS, you can install it without giving up your current working system.

Unfortunately, I haven't upgraded to Jaunty yet, so I'm not sure how much help I would be trying to debug your current situation.

---

### Post by scott29 on 2009-05-06
Thanks for the reply.  The perl script starts and I see it in the running processes when I execute it from the terminal.  No error or anything is given and I can see it is working (i.e., the process runs every 10 minutes to check for a new IP address).  

For some reason after the upgrade, the perl script isn't in the running processes after bootup, and I have to run it from the terminal.

If anybody has any other ideas, I'm all ears!

Thanks
scott29

---

### Post by scott29 on 2009-05-06
Can anybody provide any quick code that I could add to the startup script to debug this to see if it throws any errors?

I've went so far as to delete the original file and recreate it, and still it isn't working.  Very frustrating...

---

### Post by unutbu on 2009-05-06
Does ipUpdate.pl print any output to stdout or stderr? If so, you could capture it in a file by changing the upstart script command to 

```
exec perl /home/user/dnsexit/ipUpdate.pl 1>/home/user/dnsexit/ipUpdate.out 2>&1
```

---

### Post by scott29 on 2009-05-06
ipUpdate.out gets created, but it contains nothing.

---

### Post by unutbu on 2009-05-06
Perhaps edit the perl script by sprinkling things like
```

print "Got here!\n";
```

in the code. That should then be recorded in ipUpdate.out. I'm not great with perl, but if you'd like some help with this, post the script and either I or others may be able to make some suggestions.

---

### Post by scott29 on 2009-05-06
Here is the script.  Sorry it is long.  I placed the "print" statements and it prints out 2.1.  So, it seems to be erroring out in the daemonize() subroutine.  I don't know enough about Perl to decipher what that subroutine is trying to do, but my guess is something that is not compatible with 9.04.  DAMMIT why did I upgrade???!!!!  :(

```

#!/usr/bin/perl -w

###################################################

##

##  DnsExit.Com Dynamic IP update script

##  v1.6

##

##################################################



use Http_get;



$PROGRAMDIR=`dirname $0`;

chop $PROGRAMDIR;

chdir($PROGRAMDIR) || die "Unable to go to dir $PROGRAMDIR";



#

# Get config variables

#

$cfile = "/etc/dnsexit.conf";

open (CFG, "< $cfile") || (print STDERR "Fail open config file $cfile. You need to run dns-setup.pl script" && exit );

while (<CFG>)

{

  (my $line = $_ ) =~ s/\s+$//;



  if ( length( $line ) < 2 || ( $line =~ /^\s*#/ ) )

  {

    next;

  }

  ($key, $value) = split(/=/, $line);

  $keyVal{$key} = $value;

}

$ipfile   = $keyVal{"cachefile"} || '/tmp/dnsexit-ip.txt';

$pidfile  = $keyVal{"pidfile"} || '/var/run/ipUpdate.pid';

$daemon   = lc($keyVal{"daemon"}) || 'yes';

$interval = $keyVal{"interval"} || 600;

$logfile  = $keyVal{"logfile"} || '/var/log/dnsexit.log';

print "Got here 1!\n";



if ( ! ( $daemon eq "yes" ) )

{

  clear();

  $ip = getProxyIP();

  print "Got here 2!\n";

  

  $ipFlag = isIpChanged($ip);

  if ( $ipFlag == 1 )

  {

    mark("INFO", "100", "IP is not changed from last successful update");

    exit 0;

  }

  postNewIP( $ip );

}

else

{

  print "Got here 2.1!\n";
  daemonize();
  print "Got here 3!\n";

  while(1)

  {

    clear();

    mark("INFO", "100", "Started in daemon mode");

    $ip = getProxyIP();  

    $ipFlag = isIpChanged($ip);
    print "Got here 4!\n";

    if ( $ipFlag == 1 )

    {

      mark("INFO", "100", "IP is not changed from last successful update");

    } 

    else

    {

      postNewIP( $ip );
      print "Got here 5!\n";

    }

    sleep( $interval );

  }

}

exit 0;

#-----------------------------------------------------

#-- Sub Routines

#-----------------------------------------------------

sub postNewIP

{

  my $newip = shift ( @_ );

  my $get = new Http_get;

  my $url = $keyVal{"url"};

  my $login = $keyVal{"login"};

  my $password = $keyVal{"password"};

  my $host = $keyVal{"host"};

  my $posturl = "${url}?login=${login}&password=${password}&host=${host}";



  if ( $newip =~ /\d+\.\d+\.\d+\.\d+/ )

  {

    $posturl = ${posturl} . "&myip=${newip}";

  }



  my $response = $get->request($posturl);

  if ($response->is_success)

  {

    #record successful update of the ip address

    

    $result = $response->content;    

    if ( $result =~ /(\d+)=(.+)/ )

    {

      mark("Success", "$1", "$2");

      open S, "> $ipfile";

      print S $ip;

      close S;

    }

    else

    {

      mark("ERROR", "-99", "Return content format error");

    }



  }

  else

  {

    mark("ERROR", $response->code, $response->message);

  }



}



sub isIpChanged

{

  my $newip = shift(@_);

  open SS, "< $ipfile";

  my $preip = <SS>;

  close SS;

  #print "new=[$newip] old=[$preip]";

  if (!($newip eq $preip))

  {

    return 0;

  }

  return 1;

}

sub getProxyIP

{

  my $get = new Http_get;

  my $ipServs = $keyVal{"proxyservs"};

  my @servs = split(/;/, $ipServs);

  foreach $server ( @servs )

  {

    $myUrl = "http://" . $server;

    

    $response = $get->request($myUrl);

    if ($response->is_success)

    {

    	if ( $response->content =~ /\D*(\d+\.\d+\.\d+\.\d+).*/ )

    	{

    		mark("INFO", "100", "$myUrl says your IP address is: $1");

    		return ( $1 );

    	}

    	else

    	{

    		mark("ERROR", "-100", "Return message format error.... Fail to grep the IP address from ".$myUrl);

    	}

    }

  }

  mark("ERROR", "-99", "Fail to get the proxy IP of your machine");

  return "";

}

sub mark

{

    my ($type, $code, $message) = @_;

    open (LOGFILE, ">>$logfile");

    my $msg=localtime()."\t$type\t".$code."\t".$message."\n";

    print $msg;

    print LOGFILE $msg;

    close LOGFILE;

}

sub clear

{

    open (LOGFILE, "> $logfile");

    close LOGFILE;

}



# Daemonize the process and write pid to pidfile

sub daemonize {

  open (STDIN, '/dev/null')   or die "Can't read /dev/null: $!";

  open (STDOUT, '>>/dev/null') or die "Can't write to /dev/null: $!";

  open (STDERR, '>>/dev/null') or die "Can't write to /dev/null: $!";

  defined(my $pid = fork)   or die "Can't fork: $!";

  if ($pid ) {

    open (PIDFILE, ">$pidfile");

    print PIDFILE $pid;

    close PIDFILE;

    exit;

  }

  umask 0;

}

```

---

### Post by scott29 on 2009-05-06
Not sure if there is an issue in the subroutine or not.  When I run the script via the command line, it also stops at "Print 2.1", but the process then shows up in the list of running processes.

I'm at a loss and very frustrated with this and all the other issues I have since upgrading...

---

### Post by unutbu on 2009-05-06
The daemonize subroutine spawns a child process and kills the parent process. stdout and stderr is redirected to /dev/null.
This is why the print statements disappear after daemonize() is called.

Lucky for us, the rest of the script (run by the child process) writes some debugging info to a log file. Check /var/log/dnsexit.log. If that file does not exist, look inside /etc/dnsexit.conf. It should tell you the location of the log file.

If you'd like, post the log file and we can work from there.

---

### Post by scott29 on 2009-05-06
Unfortunately there is nothing in that log file regarding an error.  The only thing there is the following, which "refreshes" every 10 minutes (which is how often I have it set to check for ip changes):

Started in daemon mode
[http://ip.dnsexit.com](http://ip.dnsexit.com) says your IP address is xxx.xxx.xxx.xxx
IP is not changed from last successful upgrade

I also went back and tried the other way suggested to launch the Perl script at startup (modifying /etc/rc.local).  I got the same result, which is the process is not starting and doesn't show in the processes list.

At this point, I'm thinking of copying my data over and reinstalling 8.10.  Between this issue and the fact Terminal doesn't work, I just want my old system back :)

---

### Post by bpalone on 2009-05-08
If it is of any comfort, I am having an issue with ipUpdate from DNSexit as well.  I'm running 8.04 server and it appears to be running for 24 hours then dropping out.  I need to restart it and see if it quits again in 24 or if cron job around midnight is whacking it.  Had an issue with ip not being updated the other day and that started me on the trail.

I need to wander through the system logs and see what goes on about that time of day.

My initial thoughts at the moment, are to create cron job to restart it everyday.  If this matters, it appears that my ip doesn't change that often, once a week or so.

For $5 a month I can a static ip, but I would like to keep the $5.

---

### Post by scott29 on 2009-05-08
If you write a CRON job that works and can start the ipUpdate service at startup, please post.  I have tried so many things and nothing ever works.  I think I tried a CRON job once but I couldn't get it working, but that may have been my lack of knowledge of how to get it running.

I had this working as originally posted on Ubuntu 8.10.  Why it stopped working after the upgrade to 9.04 I have absolutely no idea.  I just added it as one more issue with 9.04 and I really wish I hadn't upgraded but it is too late now...

---

### Post by bpalone on 2009-05-08
Are you rebooting everyday?  If not, why not just remember to start ipUpdate when you do.  I had been running a Samba file server on the same machine I'm running 8.04 on for over a year without touching it.  So, Linux doesn't have to be rebooted like windows does.

I am surprised that editing the rc??? file, as mentioned early on doesn't get the job done.  I am fixing to st down with a book or two and read up on cron.  The daily is an easy one and I don't know if it is run right after a reboot or not.  Maybe someone with more knowledge than me will chime in.  Right now, I am just watching to see when ipUpdate drops out again.  If it appears to be random, then I will set up crons to run often enough to keep it running.

I will post what I find, but it will take a day or three.  If we find out that daily crons are run at reboot, then that would solve your problem.  You have to make sure your script is executable, and that is just two lines with a syntax I can't remember right now.  Let's see what turns up here and my watching for the quit/failure rate.

---

### Post by unutbu on 2009-05-08
bpalone, cron jobs are set to run at specific date/times. You can not configure cron jobs to run at boot. Instead,
/etc/local.rc or /etc/event.d/ is the place to configure your system to run scripts at boot time.

Although it would be possible to set up a cron job to run ipUpdate.pl periodically, know that ipUpdate.pl itself updates the IP every 10 minutes by default. Therefore, if ipUpdate.pl is working as it should, there is no need for a cron job. 

Also, ipUpdate.pl does not check if another copy of itself is already running. So a cron job might spawn multiple ipUpdate.pl processes. 

Have you checked /var/log/dnsexit.log to try to find out why ipUpdate.pl terminated unexpectedly?

---

### Post by bpalone on 2009-05-08
Scott29

This will start ipUpdate at bootup:

```
sudo vi /etc/rc.local
```

Add the following before the exit 0

```
/etc/init.d/ipUpdate start

```
Save and exit.

My rc.local didn't contain anything other than the remarks about it doing nothing.

edit: This is provided you followed their instructions set it up to run in daemon mode.  If not run the setup and change it.


You can use an editor other than vi, it is what I use most of the time from the command line.

---

### Post by bpalone on 2009-05-08
unutbu

It would be great if the log file had anything other than three lines.  It overwrites itself every time it runs. I had seen somewhere that someone else had had problems with dnsExit's ipUpdate terminating randomly.  

If I have to go the cron route, I was planning to do a "stop" first, then doing a "start".  

My question on starting or rebooting with cron, was: If you have a daily cron job, does the system automatically run the daily on startup or a reboot.  If it did, then that would of been an answer, although not the cleanest or best.

---

### Post by scott29 on 2009-05-10
> **bpalone said:**
> Scott29

This will start ipUpdate at bootup:

```
sudo vi /etc/rc.local
```

Add the following before the exit 0

```
/etc/init.d/ipUpdate start

```
Save and exit.

My rc.local didn't contain anything other than the remarks about it doing nothing.

edit: This is provided you followed their instructions set it up to run in daemon mode.  If not run the setup and change it.


You can use an editor other than vi, it is what I use most of the time from the command line.

This does not work on my system.  I have 9.04 installed.  Can you validate that this in fact works for you, and are you running 9.04?  

If so, what on earth can explain why it works for you and not for me?

The process is set to run in daemon mode.  After bootup, all I have in the log file is "Started in daemon mode".  The perl process does NOT show up in the list of running processes.

This is horribly frustrating...

---

### Post by bpalone on 2009-05-10
I am using 8.04 Hardy server and it works.  I tried it before I posted it.  I believe that it being set to run in daemon mode, you just use the /etc/init.d/xxxx to start whatever it is.  To verify that it is working I keep monitoring the log file, since it updates every ten minutes, the time will change in the log file.

My ipUpdate has been running for about 36 hours without failing.  Maybe, my issue was just a fluke.  I am going to keep watching it closely to see.  

You may go re-visit the newer method recited earlier in this thread.  It could be that the newer version has quit looking at the rc.local file and is just using the newer method.  However, if that were the case, I'm guessing that the rc.local file wouldn't be there.

I use the LTS releases because I figure I will have the least problems with it.  I am also a very firm believer in "IF AIN'T BROKE, DON'T FIX IT".  If you enjoy working with the latest and greatest, then by all means follow the upgrade path as it progresses.  That is a needed thing to find the bugs leading to the next LTS release.  All of us that use the LTS versions thank the ones doing this.

I recommend to anyone starting off with Ubuntu to use the LTS version for those reasons.  A new user doesn't need the aggravation of a buggy os on top of learning an entirely different os.  Likewise, if you are trying to keep a server up and running without undue headaches, I would recommend staying with the LTS versions.  But, here again, if you enjoy beating the new path, then by all means do it.  We want to thank those that do, so that we that don't have an easier life.

---

### Post by scott29 on 2009-05-10
Well, I wish I would have read your advice about a week ago!!  I don't know why I upgraded as I certainly didn't have a good reason to, and at this point I am completely regretting it.  

Both methods that are highlighted in this thread worked fine for me in 8.10.  They do not however work in 9.04.  So, it stands to reason something has happened with 9.04.  The really odd thing is I tried creating a new upstart process that simply writes out to a file, and that process works with 9.04.  So I don't know where the blame lies on why the ipUpdate perl script does not start...is it the actual script, or has something changed in the OS?

I've learned my lesson the hard way and never again will I consider upgrading.  Oh well, lesson is learned I guess.

---

