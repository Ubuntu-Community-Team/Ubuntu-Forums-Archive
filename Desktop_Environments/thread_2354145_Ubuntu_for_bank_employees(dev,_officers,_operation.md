---
title: "Ubuntu for bank employees(dev, officers, operations, sales...)"
date: 2017-02-28
forum: Desktop Environments
---

### Post by tgkprog on 2017-02-28
I had asked this on askubuntu. It was suggeted I ask on forum as its a broad question (reference [http://askubuntu.com/questions/872453/ubuntu-for-bank-dev-employees](http://askubuntu.com/questions/872453/ubuntu-for-bank-dev-employees))
Are there processes and methods documented on how to run custom  Ubuntu computers (from install to every day usage) for banks and other  businesses that do not want users to download binaries from possibly  insecure locations?

  
So that apt-get, update etc happen from only a few trusted internet or intranet locations?

  
These users are support,  novice users of systems and developers of the bank software... so some  of them need sudo privileges, to install software, run and test it, besides others who will work on a few apps, on the web or custom binaries. 
Is there a ready way to monitor them so  that any exceptions are caught quickly (like adding the sources list)  but other actions like installing stuff from known repos goes  unreported.

  Aim is to be secure, use Ubuntu or a flavour, allow developers and other sudo users to be as productive as possible. (And reduce dependence on Windows and Mac computers)

  
.2. And the IT folks can dictate policy to users so they can't do some  actions like share a folder, even if sudo user? A complete solution?

.3. Are there any examples of banks, or other financial institutions that have had success using Ubuntu as their OS for their employees desktops?

Right now most of the resistance in my company is that Ubunutu is not safe, maybe another flavour of linux (but then for me as a developer - i will lost the great ubunutu eco system, so rather have ubuntu usage tigthened up and policies applied to make it safe, with freedom to over ride any restrictions with needed.

Some apps do not work on linux. For that only recourse is to use Wine and dual boot (or virtualization), right? Or is there some new app to run windows apps on ubuntu?

---

### Post by TheFu on 2017-02-28
I don't have the necessary expertise to advise you.  But here goes anyway ... I have previously (fortune 10), but my expertise is dated.  It was a govt regulated industry in the USA. Different industries in different countries will have different regulations. Locale is critical.

I would suggest getting professional, paid, advice from someone in the banking industry, in the region of the world you are before going too far in this direction. A small, subtle, mistake can have massive repercussions wasting lots of money (time).  My E&O Professional insurance has many requirements that don't make sense, but we still do them to avoid a contract breech condition. Banking regulations must be similar and probably have books full of mandates.  

If the bank CEO and President aren't behind this effort. Stop now.  The branches will complain so much and so loudly it will never succeed. Buy in from the top is mandatory for stuff like this to be completed, even for a single branch as a trial.  If Munchin can't stay on desktop Linux with all their desire, I think we'll have to be satisfied with 65% of smartphones and 75% of internet servers (my guesses, I didn't look those numbers up).

**sudo** isn't just about gaining complete root access. It has extreme controls to allow 1 specific command for 1 user or 20 commands with 5 different options for a group or probably 500 other sudoer options.  The sudoers manpage is very good.  Many of the controls are subtle and are not sufficient to protect a system from any experience Unix person.  Even allowing a developer access to system log files can, if not setup correctly, allow them full root access. Whoever sets this up needs to by an expert in Unix.  For example, don't let people edit using sudo.  Disable that - there are multiple levels necessary to prevent it.  

I wouldn't let devs have control of their own systems or install software.  That allows way too many back doors. They can control a container or a VM completely, however. root/sudo is not necessary for those to work.  Just beware that it is possible to create a container without using root on the host, yet gain root over the host file system.  I did it yesterday on a fully patched Ubuntu 16.04 system using LXC through virt-manager.

For apps that don't work on Linux, using a remote desktop into a Windows terminal server would be my suggestion.  That way you centrally control licenses, backups, scanning, and it is just enough hassle to discourage use, while being 100% compatible.  WINE doesn't work as well for most business tools as people think.  Most effort seems to be around MS-Office and games.  Virtualization DOES work really well, but it is a hassle to manage all those Windows licenses - avoid that by centralizing them on a terminal server or 2 or 50.  

As for limiting internet access - banks shouldn't allow any of their users access to the internet directly. They need a network layered security model with different types of workers and servers on different networks that are locked off from each other.  Where I worked (not a bank), we had 6 different networks for different types of needed access.  There wasn't anyone with direct internet access. Everyone had to go through a proxy server which filtered everything. We installed an SSL cert on all client workstations so we could MITM all HTTPS connections and perform DPI. This will become more important with websites being strongly pushed by google to use HTTPS going forward.

As for apt repos. Use an internal mirror. Don't let any servers or desktops get patches from the internet.

I don't know of any step-by-step instructions. Sorry.  If I'd written all that down, it would definitely be company proprietary information.

Lastly, in a bank environment, I probably would NOT pick Ubuntu either.  Those people are correct.  I'd go with a distro that has SELinux support and a culture of using SELinux from the ground up.  As a developer, you should be flexible. After all, Linux is Linux is Linux and trading 1 proprietary jail for another isn't exactly smart, IMHO.  Use dev tools that work on all Linux systems, not just Ubuntu.  That way when the weather changes, it doesn't matter much to your solutions.  At the core, Ubuntu is a fairly normal debian system with a pretty GUI. I don't want to be rude, but if security is your primary concern, work with that AS THE PRIMARY CONCERN. 

BTW, I was a professional developer for 15 yrs and believed I knew how to run systems.  I was mistaken.  I've learned that developers should never have powerful systems. They should never be allowed onto production systems, and they shouldn't be allowed to use more than 2 languages for a solution (redhat taught me that one).

I'd also push for app servers to be deployed using automatic processes and containers - probably docker - since it has the most backing. It would be smart to use docker, but not download any docker images, if that makes sense.  You only want prebuilt images from highly trusted sources - i.e. someone you are paying and have a contract with.  Another best-practice for servers is to run the containers inside a VM.  At a conference last June, there were about 5 different "best practices" sessions around container deployment, management, security and life-cycles.  By using containers for your application deployment, you've effectively removed ubuntu-specific dependencies. [https://www.youtube.com/user/southeastlinuxfest](https://www.youtube.com/user/southeastlinuxfest)

For end-users, I wouldn't dual boot in a business environment. Make Linux the boot OS and if they want/need other apps, use a remote desktop or limited virtual machine as needed.  For developers, I'd be inclined to use dev servers, not the local desktops.  Those dev servers should be setup as close to production as possible, especially as it relates to security.


IMHO.  But I'm not qualified to advise on any of this stuff.

---

### Post by tgkprog on 2017-03-03
Great information. Yes best left to experts who know more about linux. I just want to be able to use eclipse, elastic, mysql or maria db, ... and my other tools and program in peace without the OS updating some patch and messing up something. /mywindowsstory

At least my managers are listening and will hopefully get the right advice and good quotes to get this done. In the long run should save money and give users more stability to have dual boot systems. A good personal OS Crash DRP too.

---

### Post by TheFu on 2017-03-03
Ah ... I've been there.  I worked in highly controlled environments where I wasn't given a choice for when system patches were applied.  This is why the "best practice" for development tools is not to use those that are provided by the package management system if your code is sensitive.  For example, a new libc is probably fine within the same release and 3rd level updates version x.y.z (z is is always ok), y might be ok, and x probably requires some porting effort.  This method is commonly used throughout the Unix world. Library versions **should** work that way, but often some crazy dev who doesn't care or never learned this technique and expectation won't follow it.

So in a corporate environment, everyone in the SW developer groups need to have agreed dates for moving forward between major changes.  Get your group together, raise the issues with 1st and 2nd level managers. They should understand and support you.  Someone needs the job to monitor **every** library for security updates.  It is a huge issue inside corporate dev teams to ignore security patches from external libraries. This is bad.  There are tools that will scan different types of code using lists of known security issues.  Attended an OWASP presentation about this for java last year.  Just gotta say that I'm glad I don't do java.  Perl and CPAN DO follow the 3rd level versioning and they are religious about testing of all libraries and reporting issues across all platforms automatically.

In the Perl world, we use a tool to keep our tools separate from the OS versions. It is called perlbrew.  Ruby has rvm or rbenv.  Python has something too.  With these tools, it is easy to lock versions at the x and y levels but let z changes be installed.

You'll want to manage your JAVA_HOME, PATH and LD_LIBRARY_PATH judiciously to ensure your preferred tools are found before the system tools.  No need for a whole new OS installed.  You can install eclipse into your HOME, if you like. The same for the other tools.  This was very common in the old days.  Better than having system needs for newer releases ignored.  Check out jenv and jabba, if you need a tool to manage this stuff.

And I'd like to clarify my "don't let devs install software" statement.  "Don't let devs install or manage system-level software." For their development tools, they should have development areas where everything they do is under their control, provided root isn't needed.  Apps that need root to work are an abomination. I say this with 25+ yrs experience.  Needing root just shows lazy devs, IMHO.

Make sense?

Hope this is helpful.

---

### Post by tgkprog on 2017-03-06
> **TheFu said:**
> "don't let devs install software" statement.  "Don't let devs install or manage system-level software." For their development tools, they should have development areas where everything they do is under their control, provided root isn't needed.  Apps that need root to work are an abomination. I say this with 25+ yrs experience.  Needing root just shows lazy devs

Hope this is helpful.
Very helpful. We do not use OS level software a lot. Java - can use any version. Sometimes have had an app server running on Java 5 while another runs on Java 6. Just about the current PATH and classpath as you mentioned.
We have issues with other software, like a patch making the terminal unstable, or git unstable, programs that have OS level hooks, that get corrupted so badly that the terminal (cmd.exe, command prompt) versions is effected too.

Or the Oracle Db instance box having issues after applying a few patches.

---

