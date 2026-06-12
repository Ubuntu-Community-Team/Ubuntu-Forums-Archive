---
title: "Host your own website for $1.19 with FreeDNS, DynDNS, and Google Apps"
date: 2008-12-24
forum: General Help
---

### Post by coolaj86 on 2008-12-24
You're going from a no-nothing running Ubuntu to Web-Masta' in 30 minutes.

Buckle up!

Full Tutorial with Pictures Available on Google Docs:
[Host your own website for $1.19]("http://docs.google.com/Doc?id=dc7fw57_79hmgqmn3j")

You have the link to the full tutorial so here I'm going to skim the fat and just give the stripped down instructions.

Example Personally registered domain: hasgotthe.info
Example Shared Dynamic DNS: twdp.hobby-site.org

Just a quick review on DNS:
NS - NameServer. The server that other computers look to to resolve the name to an IP address
A - IPv4 Address. If you want to specify a static ipv4 address.
AAA - IPv6 Address. If you want to specify a static ipv6 address.
CNAME - Common Name. Essentially the same as A, but you give a name for an address.
MX - Mail eXchange. The server that e-mail should go to.
resolve - What happens when the cpu fairy churns "www.hasgotthe.info" into 76.8.213.163
alias - When a CNAME record like "www.hasgotthe.info" points to another CNAME record like "twdp.hobby-site.org"

As long as you check that your domain and dyndns domain are available you can do these final steps before any of the beginning ones. I'm showing you the last step first because it's the only one that most people have a difficult time with.

Go to FreeDNS.Afraid.org
Register an account and log in.
Domains > Add > hasgotthe.info

Direct the root domain to the www domain
(Why? To be user friendly: [http://no-www.org/](http://no-www.org/))
Subdomains > hosgotthe.info (A, not MX) > Forward URL > [www.hasgotthe.info](www.hasgotthe.info)
Save

Subdomains > [www.hasgotthe.info](www.hasgotthe.info)
Type: CNAME
Destination: twdp.hobby-site.org
Save

Verify Google Apps
(you'll need to double check this when you go to create your real account)
Subdomains > Add
Type: CNAME
Subdomain: googleffffffffdc7c61a1
(or whatever random thing you got)
Destination: google.com
Save

Add any additional domains using your DynDNS address as the CNAME.
You'll use DynDNS because there's a nicer client for it than the ones for FreeDNS.

Setup Google Email for your domain.
Subdomains > mail.hasgotthe.info
Type: CNAME
Destination: aspmx.l.google.com
Save

Subdomains > Add
Type: MX
Destination: 20:alt1.aspmx.l.google.com
Save

Subdomains > Add
Type: MX
Destination: 20:alt2.aspmx.l.google.com
Save

GoDaddy.com - Domain Registration
NOTICE:
I would not recommend GoDaddy to anyone. Their homepage alone looks sketchy and you have to be very keen to uncheck and unclick the things they keep signing you up for automatically on each "Continue" page (and also once you've completed your account you have to log in and uncheck a bunch of marketing spam they sign you up for).
The only reason I'm using them here is that as of the time of this writing the .info domains are on sale for $0.99 ( + $0.20 ICAN fee).

When that sale ends, just pay the $10.00 for Google Apps registration (which, ironically, happens through GoDaddy - but without the crap) and then modify these instructions accordingly.

After you enter in your personal information and continue you'll see the N-year renewal option and some green text that asks you to click and gives you the option to use other name servers. Click that.

Even if you haven't created your FreeDNS account, you'll still want to use these name servers now.
ns1.afraid.org
ns2.afraid.org
ns3.afraid.org
ns4.afraid.org

DynDNS.org - Dynamic DNS
NOTICE:
Don't use the same password that you use for your bank account! It will be sent plain text in the clear by ddclient.

After creating your account navigate to "My Hosts" / "Host Services" 
Add a subdomain

Note:
Don't think too hard about what you want this to be called as it will only be used for CNAME lookups. No one will ever see it in their browser window.

Note:
Don't use the automatic IP detection. Set your IP to a bogus address like 127.1.1.1.

On your Ubu-box you should install and configure ddclient
```
sudo apt-get install ddclient
sudo vim /etc/ddclient.conf

# You should edit the file to look something like this:
pid=/var/run/ddclient.pid
protocol=dyndns2
use=web, web=http://whatismyip.org
server=members.dyndns.org
login=ajoneal
password='secret'
twdp.hobby-site.org

sudo /etc/init.d/ddclient start

```

Check on the Host Services Page on DynDNS.org verify that it no longer has the bogus address, but rather the one as seen on [http://whatismyip.org](http://whatismyip.org)

Sign up for Google Apps
[http://www.google.com/a/cpanel/domain/new](http://www.google.com/a/cpanel/domain/new)

Get GMail for your domain:
Click on the Activate link under Email
Follow the instructions above for FreeDNS and click Complete
10:aspmx.l.google.com
20:alt1.aspmx.l.google.com
20:alt2.aspmx.l.google.com

Verify Domain Ownership
Select CNAME verification
Follow the instructions above for FreeDNS and click Complete


Note:
If you were to use something like inadyn with FreeDNS instead of using ddclient with DynDNS you would set an A record for hasgotthe.info and a CNAME for any other subdomain. inadyn would directly update to freedns rather than requiring an additional name resolution.

Also note that these A or CNAME records could point to your same computer or to multiple computers


I hope that this has been as beneficial to you as it has been to me!

---

