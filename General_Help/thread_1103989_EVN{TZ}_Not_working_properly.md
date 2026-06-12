---
title: "EVN{TZ} Not working properly"
date: 2009-03-23
forum: General Help
---

### Post by SteelWo1f on 2009-03-23
The following perl code does not work properly on Ubuntu 8.04.

use POSIX;
$ENV{TZ} = "UTC";
my $time = strftime("%Y-%m-%d %H:%M:%S %Z", localtime(time));
print "$time\n";
$ENV{TZ} = "US/Eastern";
my $time = strftime("%Y-%m-%d %H:%M:%S %Z", localtime(time));
print "$time\n";

I get:
2009-03-23 13:21:45 UTC
2009-03-23 13:21:45 EDT

But on 8.10 and OpenBSD 3.6 I get:
2009-03-23 13:22:03 UTC
2009-03-23 09:22:03 EDT

I have tried it on both 8.04 server and desktop.

Does anybody know what the problem is here?

---

