---
title: "puppet service status checks"
date: 2011-10-20
forum: Desktop Environments
---

### Post by deesto on 2011-10-20
We've written some cross-platform Puppet manifests to ensure specific services are running, and although Puppet's providers should be able to abstract away the details for some things, it doesn't seem to be able to properly catch return codes for some services, even when the proper service name is specified for each platform (NTP is 'ntpd' in Red Hat, but 'ntp' in Ubuntu, etc.)

Even though ntp, rsyslog, and ssh are all running, when Puppet agent runs (version 2.6.8-1ubuntu1 on 11.04) in daemon mode, it always returns the same message:
*enable changed 'false' to 'true'*

So Puppet thinks the services are not running, then (re)starts them, and does the same again the next time it runs.

From checking these services manually, I assume the service checks should be done like the following:
[LIST]
[*]ntp check: /etc/init.d/ntp status
[*]rsyslog check: /sbin/status rsyslog
[*]ssh check: /sbin/status ssh
[/LIST]

Since `status` is provided by upstart and supported by Puppet, I don't understand why the inherent checks for rsyslog and ssh aren't working, and aren't using upstart, or how to fix them.

What is the "right" way to check status on these services via Puppet?  I see there was [a related bug]("https://bugs.launchpad.net/ubuntu/+source/puppet/+bug/551544") but this was fixed 1.5 years ago.

I'd also like to be able to check whether iptables is running, but this is another issue entirely, as iptables is not able to be checked in Ubuntu in a manner similar to that in Red Hat.

---

### Post by deesto on 2011-12-07
Is anyone using Puppet to manage Ubuntu services?  Can you please mention how you're checking status on services such as:
[LIST]
[*]ntp
[*]ssh
[*]rsyslog
[*]iptables
[/LIST]
Left to its own devices, Puppet uses its default handlers to check status on these, and consistently reports that these status checks return "false" and tries to restart them with each run.

---

### Post by deesto on 2011-12-17
Anyone? :(

Also wondering how people are managing upgrades to apt packages to get Puppet in a usable state with a relatively modern version, as the stock package for 11.04 is pretty old and bug-ridden.  I've been visiting the launchpad.net site for a new version of each necessary package, and downloading and installing them individually.

---

### Post by HendyIrawan on 2012-02-21
My workaround is like this:

```
service { 'neo4j-service':
	enable  => true,
	ensure  => running,
	hasrestart => true,
	hasstatus => true,
	status => '/usr/sbin/service neo4j-service status | grep "is running"',
	require => Class['neo4j']
}

```

I agree this is a Puppet bug and should be reported as bug. (is it?)

I'm using Puppet 2.7.10.

---

### Post by deesto on 2012-02-21
Right: a custom 'status' command is one way to approach this.  Unfortunately, this particular approach would not work for some of the services I've mentioned as problematic.  Also, if possible, I'd prefer a solution that would be forward-compatible as both Puppet and the service management mechanism in the OS move forward as well; using the default service handlers would be the best way forward, but perhaps that's not possible in this case.

I have seen a few related bug reports, but they either seem more focused on upstart than interested in generic 'service [foo] status' checks, or have no resolution nor indication that work is progressing.

---

### Post by HendyIrawan on 2012-02-22
I've filed it here:

* [Puppet bug #12773: Service Status detection does not always work properly on Ubuntu]("https://projects.puppetlabs.com/issues/12773")

There's also [Launchpad #551544: puppet in lucid does not support upstart status]("https://bugs.launchpad.net/ubuntu/+source/puppet/+bug/551544"), it says fixed but I don't think it's fixed. I'm using Ubuntu 11.10 with Puppet 2.7.10 and still having this problem.

---

### Post by deesto on 2012-02-22
Thanks Hendy.  I had seen the report from two years ago but dismissed it in my case, as the problem persisted despite having been "fixed".  I'm now watching both issues.

---

### Post by deesto on 2012-02-24
BTW, strangely enough, on my 11.04 workstation (w/puppet 2.6.8 ), when I run a `sudo puppet agent --test` manually from my client, all of these services return the proper response, and Puppet assumes all is well and doesn't try to restart anything.  It's only when the puppetmaster pushes a run that the status checks prompt for s service restart.  From a `debug` of my manual run I see:
```
debug: Service[rsyslog](provider=debian): Executing 'sh -c LANG=C invoke-rc.d rsyslog status | grep -q '^rsyslog.*running''
```

Should the check behavior and result be different when run locally versus pushed by a remote master?

---

### Post by sgm277 on 2012-11-13
I encountered the same issue, I am using Pupet 2.7.11 on Ubuntu 12.04, I wrote a simple manifest to install ssh and ntp and check the services.

For ntp service:

when I stop ntp service mannually, puppet can detect it and start ntp via using /etc/init.d/ntp start.

For ssh services:

When I stop ssh mannually, puppet will use /etc/init.d/ssh status to check the status of ssh, but IT DO NOTHING, ssh is still stopped. 

The interesting thing after I modified the /etc/init.d/ssh script is puppet can start ssh service by using the new start script of ssh.

what I do is echo "/etc/init.d/ssh.ori $i | grep ^ssh" >> /etc/init.d/ssh, this will make the output much easy to be read and recognized.


But what baffle me is that when I decided to use "service ssh status " instead of the above modified script ( they have the same output), Puppet was not able to start ssh :(

---

### Post by deesto on 2012-11-13
I'm sorry to hear this, as my main system is still on 11.04 but I was looking to move to 12.04 soon, which would be problematic if the default service checks are still broken.  I'm really surprised by this, actually, since there's been quite a bit of Puppet development lately, and I'm fairly certain a significant amount of that development has been done on (and for) Ubuntu.

---

### Post by sgm277 on 2012-11-13
Another insteresting thing was if I changed the service name from "ssh" to "sshd", puppet would complain that couldn't find /etc/init.d/**sshd** start script.

---

### Post by sgm277 on 2012-11-14
Anyway, if I customized the check status, puppet could start ssh successfully :)
class ssh {
package { "openssh-server":
ensure => installed,
}
service { "ssh":
    ensure  => "running",
    enable  => "true",
[B]    hasstatus => "false",
    status  => "ps -ef | grep /usr/sbin/[s]shd",[/B]
    require => Package["openssh-server"],
}
}

---

### Post by deesto on 2012-11-14
> **sgm277 said:**
> Anyway, if I customized the check status, puppet could start ssh successfully :)
```
[B]    hasstatus => "false",
    status  => "ps -ef | grep /usr/sbin/[s]shd",[/B]
```

Thanks for that, but as you know, that's a status check hack, which does, in my opinion, what the stock puppet check should be doing.  If we're going to have to rewrite service manifests in order to override built-in puppet status checks, why should we continue to use puppet in the first place?

---

