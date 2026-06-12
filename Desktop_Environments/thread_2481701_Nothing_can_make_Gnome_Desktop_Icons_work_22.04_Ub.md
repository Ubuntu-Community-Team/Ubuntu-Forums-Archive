---
title: "Nothing can make Gnome Desktop Icons work 22.04 Ubuntu"
date: 2022-12-07
forum: Desktop Environments
---

### Post by crazybear on 2022-12-07
Hello. Almost too frustrated to explain. I have tried everything reasonable I have found on internet. Others seem to have found a way to get it done. Extensions is 'installed', but it lists nothing installed and everything is 'unsupported' and will not install even if I ask it to anyway. While there are a few others that interest me, the MAIN reason to even try this is to override the HORRIBLE decision to remove desktop icons and normal folder behavior on desktop in Ubuntu gnome 22.04. I use the desktop more than most, and this has crippled me. Work arounds take forever and make using Ubuntu no longer useful to me. I need to install desktop-icons-ng-master [which also will not install - have tried many methods]. Can someone please help me install it - it would almost make the extensions not working moot, although both would be nice. On another computer I upgraded to 22.10 Ubuntu and it too would not allow for desktop-icons-ng-master-impish to be installed nor when I tried and it seemed to install it using install.sh NO desktop entry showed up in the settings. I usually do not use x.10 versions - only longterm ones, but am desperate and will use anything that works at this point. Getting it to work on Ubuntu 22.04 would be best, but as I said, desperate now and my work is falling behind due to this mess. Bad decision on the part of planners of Ubuntu IMHO!!! [more so because no work-around works for me]. Thanks. Sorry I sound frustrated - I am.  I could list all the ways I have tried, but suffice it to say every one listed anywhere on internet that seemed non-destructive to my system. I have tried it on new installations and old upgraded ones - result is the same - nada! Desktop icons are there, but can not be moved, cut and pasted, merged, etc. et al. like normal folders. I exclusively use Gnome Desktop and am sorry I abandoned 16.04....the last time things worked as I needed them to.

---

### Post by Dennis N on 2022-12-07
>  I need to install desktop-icons-ng-master [which also will not install - have tried many methods].

**Desktop Icons NG** is not an application that you install. It's a gnome-shell-extension. It's already installed by default as a system extension in Ubuntu 22.04. Install **gnome-shell-extension-manager** to manage all your gnome-shell extensions. Be sure the extension it's ON, and don't overlook the configuration dialog to set up your preferences. (see screenshot).

---

### Post by crazybear on 2022-12-07
You didn't read what I wrote. I have extension installed. Everything is empty and all possible extensions are listed as unsupported. If one tries to install 'anyway', nothing happens. My goal is to have 'normal' desktop with folders and files that can be moved, cut/pasted, renamed etc. [like Ubuntu for decades, but no longer as Linux starts to look and feel more like MS with things like snaps - don't get me started on them!.....]. I just want it to work. I am not as naive as you assume....but I am too frustrated to write poetically. If NG or DING is already installed, why does it NOT work...I can do almost nothing with the folders on my desktop!!! I can not reposition them, move one into another, etc. et al.....ad nauseam. Also, why does the category 'Desktop' NOT appear on my settings in 22.04 04 or even when I tried on another disk to upgrade to 22.10? [with Gnome 43 - not 42.5 - whatever that is in 22.04]. Others seem to be able to solve this - but I can not and do not know why.....

---

### Post by BlueAZ on 2022-12-07
Hi Crazybear,   I also am incredibly frustrated by this issue!  I have also tried everything, including Desktop Icons NG.  Makes no difference.  I also use desktop for current projects, and this change is giving me fits in 22.04.  Will someone please solve this for us???

---

### Post by Dennis N on 2022-12-08
What I noticed in your post #1 was this:

"I need to install** desktop-icons-ng-master** [which also will not install - have tried many methods]." and in the next sentence, you mention "**desktop-icons-ng-master-impish**". Since neither of those is the name for a gnome-shell extension, that is what my response addressed. Also, It reads to me as if you are thinking of these as applications. It's the only part I could comment on and I left the rest to another reader. 

Another comment: 
In Ubuntu 22.04 and 22.10, the Extension Manager normally does not show unsupported applications when you are searching - only those that are Installed, or installable (screenshot attached). It's a strange problem you have with extension support that I've not seen before. Possibly your attempts to install the packages mentioned above had some adverse effects to the system extension support. At the moment, besides that, I haven't any ideas what might be causing your problem. Someone else may come along with some suggestions.

---

### Post by mIk3_08 on 2022-12-08
My "Desktop Icon NG (DING)" is already installed by default when I added  the Extension package. I don't know what happen to your Ubuntu 22.04  LTS system same as mine, why you need to add it in your extension  package app. see image below. Regards and cheers.

---

### Post by crazybear on 2022-12-09
I use topgrade to make sure things are updated [fantastic program, by  the way], and this is what it ALWAYS says about Gnome Extensons -  perhaps there is a clue you experts understand. I do not get a single  clue from what it says......

[SIZE=4][B]Gnome Shell Extensions failed: 
    0: Command failed: `/usr/bin/gdbus call --session --dest  org.gnome.Shell.Extensions --object-path /org/gnome/Shell/Extensions  --method org.gnome.Shell.Extensions.CheckForUpdates`
   1: `/usr/bin/gdbus` failed: exit status: 1[/B][/SIZE]

---

### Post by crazybear on 2022-12-09
Not only can I not install NG, I can not install ANY Gnome extension!!! Extension Manager is installed. NG is NOT - never was and again I can not install any by any means [have tried over 50 'recipes' on internet.

---

### Post by Paddy Landau on 2022-12-09
I am puzzled by your experience. Desktop icons work by default in 22.04, so I have no idea what you did to your system to disable it.

Did you perhaps upgrade 20.04 to get to 22.04? Or was it a fresh installation? Or did you install a different flavour, e.g. Ubuntu Server or Kubuntu, and then install the Ubuntu Desktop? How specifically did you get Ubuntu 22.04?

---

### Post by #&amp;thj^% on 2022-12-09
> **crazybear said:**
> I use topgrade to make sure things are updated [fantastic program, by  the way], and this is what it ALWAYS says about Gnome Extensons -  perhaps there is a clue you experts understand. I do not get a single  clue from what it says......

[SIZE=4][B]Gnome Shell Extensions failed: 
    0: Command failed: `/usr/bin/gdbus call --session --dest  org.gnome.Shell.Extensions --object-path /org/gnome/Shell/Extensions  --method org.gnome.Shell.Extensions.CheckForUpdates`
   1: `/usr/bin/gdbus` failed: exit status: 1[/B][/SIZE]

Something along the  way just didn't work right can you try this, and post any error's back here:
```
sudo apt install --reinstall gnome-shell-extension-manager
```
Just to save time if the above command returns error free try:
```
 gsettings set org.gnome.shell disable-extension-version-validation true

```

---

### Post by Paddy Landau on 2022-12-10
@crazybear, in addition to the previous questions that I asked, please would you tell us where you got topgrade from. It isn't in the standard repositories, nor flatpak, nor snap. I'm wondering if that's what's causing your problems, because Ubuntu comes with automatic updates built in: You don't need to install something extra to update your system.

---

### Post by mIk3_08 on 2022-12-10
> **Paddy Landau said:**
> @crazybear, in addition to the previous questions that I asked, please would you tell us where you got topgrade from. It isn't in the standard repositories, nor flatpak, nor snap. I'm wondering if that's what's causing your problems, because Ubuntu comes with automatic updates built in: You don't need to install something extra to update your system. I agree with you Paddy. Maybe he has done something to the system that makes the system acts a very crazy behavior. This is not an ordinary case and as what I have observed this is the only case I've encountered with a very strange issue. Good luck. Regards and cheers.

---

### Post by #&amp;thj^% on 2022-12-10
How the heck did I not see "Topgrade" wow I'm for sure going blind.
This utility asks a tall order, meaning it updates flatpaks, snaps, firmware and apt....This just screams trouble 
One Example:
```
Flatpak failed: 
   0: Command failed: `/usr/bin/flatpak update --system`
   1: `/usr/bin/flatpak` failed: exit status: 1

```
A few of those updating failures could result in a big old can of worms
after messing with it and few hacks for my system ()All Development Sources)
```
&#8213;&#8213; 09:34:48 - Flatpak User Packages &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
Looking for updates&#8230;

Nothing to do.

&#8213;&#8213; 09:34:48 - Flatpak System Packages &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
Looking for updates&#8230;

Nothing to do.

&#8213;&#8213; 09:34:55 - Firmware upgrades &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
Firmware metadata last refresh: 20 hours ago. Use --force to refresh again.
Devices with no available firmware updates: 
 &#8226; System Firmware
 &#8226; UEFI Device Firmware
Devices with the latest available firmware version:
 &#8226; UEFI dbx
No updates available

&#8213;&#8213; 09:34:57 - Summary &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
System update: OK
config-update: OK
Flatpak: OK
Firmware upgrades: OK

```
There is just no way I'd trust this on my system, if i want it stable.
```
topgrade --help
Topgrade 10.2.2

USAGE:
    topgrade [OPTIONS]

OPTIONS:
    -c, --cleanup
            Cleanup temporary or old files

        --config <PATH>
            Alternative configuration file

        --config-reference
            Show config reference

        --custom-commands <NAME>...
            Run only specific custom commands

        --disable <STEP>...
            Do not perform upgrades for the given steps
            
            [possible values: asdf, atom, brew_cask, brew_formula, bun, bin, cargo, chezmoi,
            chocolatey, choosenim, composer, conda, config_update, containers, custom_commands,
            deb_get, distrobox, deno, dotnet, emacs, firmware, flatpak, flutter, fossil, gcloud,
            gem, ghcup, github_cli_extensions, git_repos, go, guix, haxelib, gnome_shell_extensions,
            home_manager, jetpack, julia, juliaup, kakoune, krew, macports, mas, micro, myrepos,
            nix, node, opam, pacdef, pacstall, pearl, pipx, pip3, pkg, pkgin, powershell, protonup,
            raco, rcm, remotes, restarts, rtcl, ruby_gems, rustup, scoop, sdkman, sheldon, shell,
            snap, sparkle, spicetify, stack, system, tldr, tlmgr, tmux, toolbx, vagrant, vcpkg, vim,
            winget, wsl, yadm]

        --disable-predefined-git-repos
            Don't pull the predefined git repos

        --edit-config
            Edit the configuration file

        --env <NAME=VALUE>...
            Set environment variables

    -h, --help
            Print help information

    -k, --keep
            Prompt for a key before exiting

        --log-filter <LOG_FILTER>
            Tracing filter directives.
            
            See: https://docs.rs/tracing-subscriber/latest/tracing_subscriber/struct.EnvFilter.html
            
            [default: info]

    -n, --dry-run
            Print what would be done

        --no-retry
            Do not ask to retry failed steps

        --only <STEP>...
            Perform only the specified steps (experimental)
            
            [possible values: asdf, atom, brew_cask, brew_formula, bun, bin, cargo, chezmoi,
            chocolatey, choosenim, composer, conda, config_update, containers, custom_commands,
            deb_get, distrobox, deno, dotnet, emacs, firmware, flatpak, flutter, fossil, gcloud,
            gem, ghcup, github_cli_extensions, git_repos, go, guix, haxelib, gnome_shell_extensions,
            home_manager, jetpack, julia, juliaup, kakoune, krew, macports, mas, micro, myrepos,
            nix, node, opam, pacdef, pacstall, pearl, pipx, pip3, pkg, pkgin, powershell, protonup,
            raco, rcm, remotes, restarts, rtcl, ruby_gems, rustup, scoop, sdkman, sheldon, shell,
            snap, sparkle, spicetify, stack, system, tldr, tlmgr, tmux, toolbx, vagrant, vcpkg, vim,
            winget, wsl, yadm]

        --remote-host-limit <REGEX>
            A regular expression for restricting remote host execution

        --show-skipped
            Show the reason for skipped steps

        --skip-notify
            Skip sending a notification at the end of a run

    -t, --tmux
            Run inside tmux

    -v, --verbose
            Output debug logs. Alias for `--log-filter debug`

    -V, --version
            Print version information

    -y, --yes [<STEP>...]
            Say yes to package manager's prompt
            
            [possible values: asdf, atom, brew_cask, brew_formula, bun, bin, cargo, chezmoi,
            chocolatey, choosenim, composer, conda, config_update, containers, custom_commands,
            deb_get, distrobox, deno, dotnet, emacs, firmware, flatpak, flutter, fossil, gcloud,
            gem, ghcup, github_cli_extensions, git_repos, go, guix, haxelib, gnome_shell_extensions,
            home_manager, jetpack, julia, juliaup, kakoune, krew, macports, mas, micro, myrepos,
            nix, node, opam, pacdef, pacstall, pearl, pipx, pip3, pkg, pkgin, powershell, protonup,
            raco, rcm, remotes, restarts, rtcl, ruby_gems, rustup, scoop, sdkman, sheldon, shell,
            snap, sparkle, spicetify, stack, system, tldr, tlmgr, tmux, toolbx, vagrant, vcpkg, vim,
            winget, wsl, yadm]



```

---

### Post by Paddy Landau on 2022-12-10
I've been looking for topgrade to see what the OP was talking about.

If it's [this one]("https://github.com/r-darwish/topgrade"), it's out of date, unmaintained, and deprecated, so shouldn't be used anyway.

If it's [this one]("https://github.com/topgrade-rs/topgrade"), it's unsuitable for Ubuntu, because it's entirely unnecessary. Maybe it's useful for something like Arch? I don't know. But in Ubuntu, it duplicates a mechanism that already exists, works, and is extensively tested. Thus, I cannot say what topgrade will actually do to your system. **I strongly recommend that you uninstall topgrade.** You should use Ubuntu's default automatic update system instead. If you prefer manual updates, you can turn off the automatic update system and update manually *using Ubuntu's default system*.

There is no need to mess with the automatic updates in Ubuntu.

But, OP, please answer our previous questions, because we cannot help you otherwise. What you are experiencing is abnormal. You must have done something to your system to cause this problem. Without further information, we can't help you to fix it.

---

### Post by #&amp;thj^% on 2022-12-10
Hopefully they will listen, Paddy this one is the current:[https://itsfoss.com/topgrade/](https://itsfoss.com/topgrade/)
Things we do for ease-of use often cause the most harm.
EDIT: I wouldn't even use this on Arch, or any system I install....

---

### Post by Paddy Landau on 2022-12-10
> **1fallen said:**
> … this one is the current:[https://itsfoss.com/topgrade/](https://itsfoss.com/topgrade/)
Ah, thanks.
> **1fallen said:**
> Things we do for ease-of use often cause the most harm.
Indeed. I can't imagine why anyone would want this on Ubuntu.

---

### Post by mIk3_08 on 2022-12-10
> **Paddy Landau said:**
> I've been looking for topgrade to see what the OP was talking about.

If it's [this one]("https://github.com/r-darwish/topgrade"), it's out of date, unmaintained, and deprecated, so shouldn't be used anyway.

If it's [this one]("https://github.com/topgrade-rs/topgrade"), it's unsuitable for Ubuntu, because it's entirely unnecessary. Maybe it's useful for something like Arch? I don't know. But in Ubuntu, it duplicates a mechanism that already exists, works, and is extensively tested. Thus, I cannot say what topgrade will actually do to your system. **I strongly recommend that you uninstall topgrade.** You should use Ubuntu's default automatic update system instead. If you prefer manual updates, you can turn off the automatic update system and update manually *using Ubuntu's default system*.

There is no need to mess with the automatic updates in Ubuntu.

But, OP, please answer our previous questions, because we cannot help you otherwise. What you are experiencing is abnormal. You must have done something to your system to cause this problem. Without further information, we can't help you to fix it. I think topgrade was good but it is no longer maintained. This might bring you to inconvenience to your system. Hope you can elaborate more about your issue and response in asap as what paddy says cause many of the community are wiling to help you. Regards and cheers.

---

### Post by crazybear on 2022-12-12
Paddy, I too am puzzled. I have tried BOTH [on separate disks] upgrade and fresh install. I do NOT use any strange flavo[u]r. Something is obviously blocking desktop icons from 'working' on my system - and I was hoping someone here/there could help me find out what it was and correct it. As you can see, others [above] have had the same problem - I am NOT alone in this problem. For me it is very upsetting and makes my work on the computer very difficult. I can and do move things from one folder on the desktop to another - if as infrequently as possible AND with GREAT difficulty by navigating through places and then finding copy to or move to...etc. It is NOT supposed to be that way. I even tried on yet a third partition to install fresh 22.10 to see if that would work. It did not. Could some hardware problem be causing this? I would doubt it - it must be some 'simple' software problem, but finding it is NOT easy...I have worked on this myself for months and perhaps in my MANY attempts have confused [screwed-up] my main system. It otherwise works fine - or if there is a problem, I can fix it. The desktop icons have resisted any fix at all. Mystery. Perhaps a curse of some kind from aliens from another space-time, but more likely some unseen blocking of the 'desktop icons' [sub]program. Anyone know some interesting command line way to find out what is going on deep in the 'mind' of my processor?! Many thanks in advance.....

---

### Post by crazybear on 2022-12-12
I am not sure exactly where I came across the suggestion of topgrade. I am 98% sure it was from 'its foss' website, which sends me updates weekly. There was NO warning that it was good or problematic with certain flavors of Linux and the author raved about it. It has not caused any problems I can see. The problem with desktop icons FAR, FAR predates the recent addition of topgrade [in an attempt to cure the desktop icon problem (in part). I can, of course, remove it, but I am sure it will make no difference. I had the desktop icon problem for MONTHS before I even knew of or had installed topgrade.

---

### Post by crazybear on 2022-12-12
[COLOR=#0000ff][I][FONT=arial]rustup unchanged - 1.25.1

info: syncing channel updates for 'stable-x86_64-unknown-linux-gnu'
info: checking for self-updates

  stable-x86_64-unknown-linux-gnu unchanged - rustc 1.65.0 (897e37553 2022-11-02)

info: cleaning up downloads & tmp directories

&#8213;&#8213; 12:34:11 - Cargo &#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;&#8213;
    Updating registry 'https://github.com/rust-lang/crates.io-index'

Package       Installed  Latest   Needs update
cargo-update  v11.1.1    v11.1.1  No
topgrade      v10.2.2    v10.2.2  No

==================================================
[/FONT][/I][/COLOR][COLOR=#00ff00]*[FONT=arial]This above is from topgrade, showing its versions[/FONT]*[/COLOR][COLOR=#0000ff][I][FONT=arial]
======================================================
I just ran the re-install [although I must have done so myself a few times]....will reboot and report.
Sorry I am a bit slow in sometimes responding. I am both ill and deeply involved in a complex legal problem in a 'foreign' land and I as my own lawyer.....causing me lots of problems, but not thse here, anyway.
[/FONT][/I][/COLOR][COLOR=#ff0000][I][FONT=arial]
Just rebooted - no change!!![/FONT][/I][/COLOR][COLOR=#0000ff][I][FONT=arial]  
[/FONT][/I][/COLOR]

---

### Post by Paddy Landau on 2022-12-12
> **crazybear said:**
> I even tried on yet a third partition to install fresh 22.10…
Stick to the LTS version at this point, 22.04. I wouldn't recommend an interim release such as 22.10. It works perfectly on 22.04, so that's your starting point if you wish to use a fresh installation. (If you have sufficient RAM, you can use VirtualBox to install 22.04 in a virtual machine to test.)
> **crazybear said:**
> Could some hardware problem be causing this?
No.

You still haven't answered some questions. I repeat:

[LIST]
[*]Did you perhaps upgrade 20.04 to get to 22.04?
[*]Or was it a fresh installation?
[*]Or did you install a different flavour, e.g. Ubuntu Server or Kubuntu, and then install the Ubuntu Desktop?
[*]How specifically did you get Ubuntu 22.04?
[/LIST]
Obviously, I can't see or mess around with your system. But, given everything that you've told us so far, I rather suspect that [FONT=courier new]topgrade[/FONT] has indeed caused problems.

For future, please never install packages unless they are from the standard repositories, unless you absolutely *know* what you are doing. You can always ask here on these forums if you are considering a new package; had you done so with [FONT=courier new]topgrade[/FONT], you would have been warned to avoid it.

So…

1. Uninstall any nonsense that you've installed such as [FONT=courier new]topgrade[/FONT], [FONT=courier new]desktop-icons-ng-master[/FONT] and [FONT=courier new]desktop-icons-ng-master-impish[/FONT].

2. Additionally, you might want to purge the PPAs where you got them from: They aren't on the standard repositories, so who knows what other nonsense was added when you added them? To purge a PPA that you have added:
```
sudo apt update
sudo ppa-purge ppa:[name of the PPA]
```
Repeat the last line for every PPA in question.

This should revert packages installed or updated from those PPAs to the default, which might mean downgrading a couple of packages. I'm hoping that this will remove the nonsense that you installed, while replacing it with the default Ubuntu packages.

3. After all that, run the standard Ubuntu upgrades as follows:
```
sudo apt update
sudo apt upgrade
sudo apt autoremove
sudo snap refresh
flatpak update     # Only if you use flatpak.
```

4. If not already installed, install Extension Manager:
```
[FONT=var(--ff-mono)]sudo apt install gnome-shell-extension-manager[/FONT]
```

5. Now, reboot before you continue.

6. Open Extension Manager and check which extensions you have installed. Specifically check for anything to do with desktop icons. The *only* one that you want to see should be near the bottom, under the category "System Extensions", named "Desktop Icons NG (DING)" by ding[at]rastersoft.com, and it should be turned on. See my screenshot; yours should look the same.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291410&stc=1[/IMG]
If you see anything else to do with desktop icons, especially in the "User-Installed Extensions" category, this will cause a problem.

Open the settings (the cog wheel) to set your preferences.

Let us know what happens and what you see.

---

### Post by #&amp;thj^% on 2022-12-12
> **crazybear said:**
> I am not sure exactly where I came across the suggestion of topgrade. I am 98% sure it was from 'its foss' website, which sends me updates weekly. There was NO warning that it was good or problematic with certain flavors of Linux and the author raved about it. It has not caused any problems I can see. The problem with desktop icons FAR, FAR predates the recent addition of topgrade [in an attempt to cure the desktop icon problem (in part). I can, of course, remove it, but I am sure it will make no difference. I had the desktop icon problem for MONTHS before I even knew of or had installed topgrade.
Your probably right no harm from Topgrade, knee jerk reaction from me, please see my findings here: [https://ubuntuforums.org/showthread.php?t=2481893](https://ubuntuforums.org/showthread.php?t=2481893)
I just had to set the records right here.

---

### Post by crazybear on 2022-12-15
> **Paddy Landau said:**
> Stick to the LTS version at this point, 22.04. I wouldn't recommend an interim release such as 22.10. It works perfectly on 22.04, so that's your starting point if you wish to use a fresh installation. (If you have sufficient RAM, you can use VirtualBox to install 22.04 in a virtual machine to test.)

No.

You still haven't answered some questions. I repeat:
[COLOR=#0000ff]
====> No, I did answer your question - NO, fresh install [actually tried SEVERAL of them] 22.04![/COLOR]


[LIST]
[*]Did you perhaps upgrade 20.04 to get to 22.04?
[*]Or was it a fresh installation?
[*]Or did you install a different flavour, e.g. Ubuntu Server or Kubuntu, and then install the Ubuntu Desktop?
[*][COLOR=#0000ff]
[/COLOR]
[/LIST]
[COLOR=#0000ff]====> I answered that too - NO special anything 22.04 LTS Ubuntu flavor. Yes, some other desktops [or parts of them] are installed, but have not been used.[/COLOR]



[LIST]
[*]How specifically did you get Ubuntu 22.04?
[*][COLOR=#0000ff]
[/COLOR]
[/LIST]
[COLOR=#0000ff]====> From the official Ubuntu website for 22.04.[/COLOR]


Obviously, I can't see or mess around with your system. But, given everything that you've told us so far, I rather suspect that [FONT=courier new]topgrade[/FONT] has indeed caused problems.
[COLOR=#0000ff]
=====> As I have said twice, I doubt it. Topgrade was installed RECENTLY, the problem with the desktop icons is MONTHS old.[/COLOR]

For future, please never install packages unless they are from the standard repositories, unless you absolutely *know* what you are doing. You can always ask here on these forums if you are considering a new package; had you done so with [FONT=courier new]topgrade[/FONT], you would have been warned to avoid it.

So…

1. Uninstall any nonsense that you've installed such as [FONT=courier new]topgrade[/FONT], [FONT=courier new]desktop-icons-ng-master[/FONT] and [FONT=courier new]desktop-icons-ng-master-impish[/FONT].

2. Additionally, you might want to purge the PPAs where you got them from: They aren't on the standard repositories, so who knows what other nonsense was added when you added them? To purge a PPA that you have added:
```
sudo apt update
sudo ppa-purge ppa:[name of the PPA]
```
Repeat the last line for every PPA in question.

This should revert packages installed or updated from those PPAs to the default, which might mean downgrading a couple of packages. I'm hoping that this will remove the nonsense that you installed, while replacing it with the default Ubuntu packages.

3. After all that, run the standard Ubuntu upgrades as follows:
```
sudo apt update
sudo apt upgrade
sudo apt autoremove
sudo snap refresh
flatpak update     # Only if you use flatpak.
```

4. If not already installed, install Extension Manager:
[COLOR=#0000cd]
=====> LONG AGO installed - can do nothing.[/COLOR]
```
[FONT=var(--ff-mono)]sudo apt install gnome-shell-extension-manager[/FONT]
```

5. Now, reboot before you continue.

6. Open Extension Manager and check which extensions you have installed. Specifically check for anything to do with desktop icons. The *only* one that you want to see should be near the bottom, under the category "System Extensions", named "Desktop Icons NG (DING)" by ding[at]rastersoft.com, and it should be turned on. See my screenshot; yours should look the same.
[COLOR=#0000cd]
======As I have said, I have extension manager [even showed image] and it shows NO extensions and lists ALL possible extensions as 'incompatible' and will not install them.[/COLOR]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291410&stc=1[/IMG]
If you see anything else to do with desktop icons, especially in the "User-Installed Extensions" category, this will cause a problem.

Open the settings (the cog wheel) to set your preferences.

Let us know what happens and what you see.
[COLOR=#0000cd]
=====While frustrating what I have said before was not read or understood, and while I think this is a fruitless exercise, I may try it. What I would like is someone to tell me what CLI line to GREP what is and is not in my system that should or should not be regarding this issue. From the moment it was installed and rebooted the desktop did NOT work and it took me days to even get ANY desktop icons on - but they are static, one can not drag-and-drop or move to new position or open them or merge them or do most 'usual' things that could be done in the past. Thanks for the effort.......I do not think topgrade is making any problems and is correctly updating everything and reporting that it can not upgrade gnome extensions.[/COLOR]

---

### Post by crazybear on 2022-12-15
...By the way, this is where I followed instructions [there are two branches of instructions and very carefully researched which was correct for me] for installing topgrade:
[https://itsfoss.com/topgrade/](https://itsfoss.com/topgrade/)

...I am also not a 'new user'...but I am also not an expert or coder nor do I know all the inner workings of ubuntu as some of you do.

---

### Post by tea for one on 2022-12-16
How about conducting a little experiment:-

Boot into a clean, live session of Ubuntu 22.04.
Open Software & Updates.
Check that all repositories (main, universe, restricted and multiverse) are active.
Open a terminal and enter the following.
```
sudo apt install gnome-shell-extension-manager
```
Close terminal if successfully installed.
Click Show Applications > Extension Manager > Desktop Icons NG (DING) > Click gear wheel 
Screenshot herewith

Any joy?

---

### Post by Paddy Landau on 2022-12-16
> **tea for one said:**
> How about conducting a little experiment
That's an excellent idea! In addition to that, also check if you can manipulate the desktop icons as required.

If these tests fail, it might be worth checking if you have downloaded the ISO correctly.

I would add that you should use 22.04, not 22.10, because the former is a stable LTS while the latter isn't a stable release.

---

### Post by crazybear on 2023-03-16
I'm back after a long and frustrating silence. Nothing has changed. I think your [several of you] obsession with topgrade was off topic. There is NO WAY I have found to get gnome extensions to work at all on all three of my computers [each installed separately] all running 20.04.2 now. The desktop shows icons - BUT THEY CAN DO NOTHING AT ALL! VERY FRUSTRATING. If I open extension manager it shows no extensions installed and if I go to 'browse' EVERY extension is listed as incompatible. HELP! please. I am used to working with folders on my desktop. I hate to have to open desktop from places and then move or find things. That defeats the idea of having folders on the desktop - no? I just hate using 20.04 because of this [and snaps too...but that is another issue for another time]. I need to use the desktop for icons I can move [they do NOT move]; open [they do not open]; and combine one into another etc. [no such thing is possible]. You say DING is part of 22.04 - but it seems not to be in mine or is being blocked by something else. All ISOs of Ubuntu I get from the official Ubuntu website - please don't assume [as I see] that I am that naive. I have tried 30 different things to get gnome extensions to work on all three computers and all three do not have it working. They each have different hardware. I have tried downloading a new version of 22.04 and the last computer even was installed with 22.04.2 and it still is the same as the other two. I do not understand and sense no one here understands or believes me. What can I print out to show the problem and find a solution? Please. Thanks in advance.

---

### Post by Paddy Landau on 2023-03-16
> **crazybear said:**
> … all running 20.04.2 now.
May I ask why you didn't use 22.04? It is most definitely fixed there, and everything is more up-to-date.

Otherwise, you need to install the updated extension on 20.04. Let me know if you want the details for how to do this.

---

### Post by crazybear on 2023-03-17
There seems to be a lack of communication. ONCE [only] for a few days did I use [try] 22.10. For a year I have been fighting with this and throughout that time ALWAYS with 22.04! So, I do not understand why you are asking me why I do not use 22.04 - when that is all I use on multiple computers. I'm sorry I left and now can not return to 16.04. People talk about seeing a menu selection for 'desktop' in settings. There is NO such offer. Why can I NOT - repeat NOT get gnome extensions to work. I have over and over and over installed the multiple files needed. I does not work on my computerS. I have actually re-installed about 50 times and I'm getting tired and at my wits end. The only thing I can guess is that I routinely add some program which blocks both desktop icons working and at the same time extensions - though that sounds very odd to me. I did try 18.04 and 20.04 [as one time I upgraded from 16.04 - and NO none of my computers now is an upgrade - all are installed with 20.04 from the get-go. I mention this as I did not notice desktop icons working in them and I do not want to re-install again. Experts say a re-installation is a few hours work - well not for me and my configuration - maybe a few weeks to get it back to something looking almost like what I had - and I can NOT afford the time, I must work and until it is stable I can not really work. My most important computer's installation is currently unstable and crashes much too much of the time. That is another issue I have not mentioned. On my main desktop 22.04 is still crashing at odd moments. The other two computers seem stable.  I have re-installed over ten times on the desktop and am not about to try 11 - as I need to work, as I said. My laptop - which is very difficult to do my work on is the most stable - but is still has NO use of desktop icons/folders [they just sit there and I could have painted them on] or gnome extensions. It says Gnome version 42.5, but in some screen I have often seen - and can not remember now - sorry - for Gnome version is only shows a question mark. Sorry I sound upset - I am - not at those trying to help here, but at unknown gremlins who seem to be making Ubuntu more and more like Windows where one does not get to choose how the system looks and works, but I digress. I was perfectly happy with 16.04 but was aware I was missing out on all kinds of new 'things'....but those 'things' elude me and I spend too much time fighting with Ubuntu and not getting work done. I'm frustrated and exhausted. Sorry. Don't take it personally anyone.

---

### Post by Paddy Landau on 2023-03-17
OK, your comments indicate to me that you are doing something to cause this issue, because it's not normal.The fact that it takes you weeks to tailor your system to your requirements is a major indicator of a problem.

Ubuntu is designed to be the sort of system that "just works", and is intended for only minor tweaks. Kind of like Windows, Mac, and Android. You wouldn't spend weeks setting up any of them, and the same concept applies to Ubuntu.

[LIST]
[*]If the desktop icons aren't working in 22.04, *you have done something to cause that*.
[*]If they aren't working in 20.04, I can give you instructions to replace them with the updated version; just *let me know if you want the instructions*.
[/LIST]
So, if you're wanting to go to those extremes in setting up a system, then I think that maybe Ubuntu isn't the right distro for you. You might find that Arch is the better OS for you, because it's designed to be ideal for people who want to take complete control and modify their systems to a fine degree.

It's your decision at this point. Either try a distro other than Ubuntu, probably non-Debian (e.g. Arch, Mandora, Fedora) or even a non-Gnome derivative such as Kubuntu, Xubuntu or Lubuntu; or think carefully about how you are modifying your system.

*If* you decide to reinstall 22.04 (which I don't think that you will, but maybe), then test your desktop icons *before* you tweak anything at all. Even before you run the updates, and again before you run the built-in updates. Then, *each time* you tweak something, or install a new app, etc., re-test the desktop icons to discover what it is that causes them to fail.

**Final point…**

I don't know if it's already been mentioned in this thread, but have you ensured that you have a valid ISO? When you download the ISO, you need to verify its checksum:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
This is vital, because ISOs can be corrupt for several reasons. For example, a few years ago, I downloaded an ISO from an official mirror, but the mirror in fact had a corrupt ISO. I kept getting weird errors after installation until I checked the checksum and realised that the ISO was invalid.

---

### Post by DuckHook on 2023-03-17
The following may be harsh, but there is no gentle way to state it:

On this and numerous other threads, you have implored the help of forum members without reciprocating with due care or follow&#8209;through.

[LIST]
[*]You continually post walls of text with run&#8209;on sentences that are tiresome to read.
[*]You further force helpers to go fishing for your few, incomplete data points amidst a sea of high drama, irrelevant digressions, seething exasperation and rude SHOUTING.
[*]You've been asked for further information. You refuse to provide it.
[*]You've been given good advice to stop using Topgrade. You refuse to follow it.
[*]You've been told to use a LiveUSB for testing and analysis. You haven't done so.
[/LIST]
In light of the above, it goes to the credit of our helpful members that you get any replies at all.

Doing the simplest websearch on your error message returned the following as the very first hit: [https://github.com/r-darwish/topgrade/issues/779](https://github.com/r-darwish/topgrade/issues/779)

In other words, Topgrade screws up Gnome shell extensions. This effects others; not just you. Get rid of it. If you insist on using it, then you are on you own and must stop wasting everyone else's time.

I will offer the following advice only once:

[LIST]
[*]You should leave your install in its pristine default state. Stop adding garbage to it. By adding bells and whistles, you force instability onto your system that you are not equipped to deal with.
[*]The members here cannot reproduce your problem. Websearches are also drawing blanks. This heavily implies that you are doing something unusual to your installs, either during or immediately afterwards.
[*]If you monkey around trying out your own fixes, then don't come asking for help. No one can help you after you have messed up your system with days, weeks or months of who&#8209;knows&#8209;what "solutions".
[*]If you are serious about requesting help, then stick to posting just the facts and the data. Facts and data include your HW specs, how and where you download your ISO, what options you use to install and any errors in your logs.
[*]If you want help on these forums, then do so with netiquette. If you post with all caps, large screaming fonts or inconsiderate walls of run&#8209;on text, then expect your help requests to be ignored.
[*]Most of all, nix the melodrama. We are a technical help forum, not your therapist.
[/LIST]

---

