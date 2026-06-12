---
title: "Using a (Perl) script to get my IP address"
date: 2006-10-08
forum: Desktop Environments
---

### Post by srunni on 2006-10-08
Hi,

I downloaded a theme for SuperKaramba, and I was modifying it to fit my needs. It is a general purpose system information theme, and one of the capabilites it comes with is displaying the user's IP address. This is done by means of a Perl script that also comes with the theme download. However, when I start up the theme, the IP address that shows up is my network IP address, not my universal IP address. Is it possible to modify the original script so that it gets my universal IP address? Here's the code for the Perl script that is right now showing my network IP:
```

#!/usr/bin/perl

$net = `/sbin/ifconfig | grep 'eth0'`;
if (length($net))
{
	$net = `/sbin/ifconfig eth0 | grep 'inet addr'`;
	if (!length($net))
	{
	   $net = `/sbin/ifconfig eth0 | grep 'inet end.'`;
	}
	if (length($net))
	{
	   chop($net);
	   @netip = split/:/,$net;
	   $netip[1] =~ /(\d{1,3}).(\d{1,3}).(\d{1,3}).(\d{1,3})/;
	   $ip = $1 .".". $2 .".". $3 .".". $4;
	   print "". $ip ."\n";
	}
	else
	{
	   print "Not Found\n";
	}
}
else
{
   print "Error\n";
}
```

---

