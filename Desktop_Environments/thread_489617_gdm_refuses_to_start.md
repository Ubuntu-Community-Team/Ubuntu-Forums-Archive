---
title: "gdm refuses to start?"
date: 2007-07-01
forum: Desktop Environments
---

### Post by mozz on 2007-07-01
Hi,

just got linux running on my T61 Thinkpad, but when gdm starts you see the login screen flashing on the screen and then the system returns to console...according to ps -A gdm is still running...

here is the gdm debug info:

> Jul  1 21:14:18 lenovo-t61 gdm[3431]: mainloop_sig_callback: Got signal 10
Jul  1 21:14:18 lenovo-t61 gdm[3431]: GDM wird neu gestartet â\200Š
Jul  1 21:14:18 lenovo-t61 gdm[3431]: gdm_final_cleanup
Jul  1 21:14:18 lenovo-t61 gdm[3431]: gdm_display_unmanage: Stopping :0 (slave pid: 0)
Jul  1 21:14:18 lenovo-t61 gdm[3431]: gdm_display_unmanage: Display stopped
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key debug/Enable to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/Greeter to string /usr/lib/gdm/gdmgreeter
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key xdmcp/ProxyReconnect to string <NULL>
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/ShowLastSession to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/GraphicalThemedColor to string #76848F
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/InfoMsgFont to string <NULL>
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/AutomaticLogin to string <NULL>
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key xdmcp/Willing to string /etc/gdm/Xwilling
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/XineramaScreen to integer 0
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/Logo to string /usr/share/pixmaps/gdmDebianLogo.xpm
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/Xnest to string /usr/bin/Xephyr -audit 0
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/SoundOnLoginFile to string <NULL>
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/HaltCommand to string /sbin/shutdown -h now "Shut Down via gdm."
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/BackgroundRemoteOnlyColor to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key xdmcp/MaxPending to integer 4
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/Chooser to string /usr/lib/gdm/gdmchooser
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/SuspendCommand to string /usr/bin/apm --suspend
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/SoundOnLoginSuccess to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key xdmcp/MaxSessions to integer 16
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key gui/MaxIconWidth to integer 128
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/SoundOnLoginFailure to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/GraphicalThemeDir to string /usr/share/gdm/themes/
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key xdmcp/MaxWait to integer 15
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/XKeepsCrashing to string /etc/gdm/XKeepsCrashing
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/LocaleFile to string /etc/gdm/locale.conf
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandNoRestart0 to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/FlexibleXServers to integer 5
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key chooser/ScanTime to integer 4
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandNoRestart1 to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/Configurator to string /usr/sbin/gdmsetup --disable-sound --disable-crash-dialog
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandNoRestart2 to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandNoRestart3 to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandNoRestart4 to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key security/AllowRoot to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandNoRestart5 to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandNoRestart6 to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandNoRestart7 to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key xdmcp/DisplaysPerHost to integer 2
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/LockPosition to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandNoRestart8 to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandNoRestart9 to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key chooser/AllowAdd to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/InfoMsgFile to string <NULL>
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/DoubleLoginWarning to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/RemoteWelcome to string Welcome to %n
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/FailsafeXServer to string <NULL>
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/TimedLoginDelay to integer 30
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/BackgroundProgram to string <NULL>
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/SoundOnLoginFailureFile to string <NULL>
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/RebootCommand to string /sbin/shutdown -r now "Rebooted via gdm."
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/SoundProgram to string /usr/bin/play
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/IncludeAll to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key chooser/Multicast to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/XnestUnscaledFontPath to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/RemoteGreeter to string /usr/lib/gdm/gdmlogin
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/Quiver to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/DisplayLastLogin to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/Group to string gdm
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/SoundOnLogin to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/UserAuthFile to string .Xauthority
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/DefaultSession to string default.desktop
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/PidFile to string /var/run/gdm.pid
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/Use24Clock to string auto
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/RootPath to string /usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/DefaultWelcome to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key debug/Gestures to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/PositionX to integer 0
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/SetPosition to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/PostSessionScriptDir to string /etc/gdm/PostSession/
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/PositionY to integer 0
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key security/CheckDirOwner to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/PostLoginScriptDir to string /etc/gdm/PostLogin/
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/GraphicalThemeRand to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/TimedLogin to string <NULL>
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key xdmcp/MaxPendingIndirect to integer 4
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/TimedLoginEnable to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/SystemMenu to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/KillInitClients to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLRLabel0 to string Spezialbefehl _0 ausfÃŒhren
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLRLabel1 to string Spezialbefehl _1 ausfÃŒhren
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLRLabel2 to string Spezialbefehl _2 ausfÃŒhren
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key xdmcp/Enable to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLRLabel3 to string Spezialbefehl _3 ausfÃŒhren
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/AutomaticLoginEnable to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLRLabel4 to string Spezialbefehl _4 ausfÃŒhren
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLRLabel5 to string Spezialbefehl _5 ausfÃŒhren
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/DefaultRemoteWelcome to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/VTAllocation to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key security/DisallowTCP to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLRLabel6 to string Spezialbefehl _6 ausfÃŒhren
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/RestartBackgroundProgram to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLRLabel7 to string Spezialbefehl _7 ausfÃŒhren
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/SoundOnLoginSuccessFile to string <NULL>
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLRLabel8 to string Spezialbefehl _8 ausfÃŒhren
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key security/UserMaxFile to integer 65536
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/BackgroundImage to string <NULL>
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLRLabel9 to string Spezialbefehl _9 ausfÃŒhren
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/ConsoleCannotHandle to string am,ar,az,bn,el,fa,gu,hi,ja,ko,ml,mr,pa,ta,zh
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/ChooserButtonLogo to string /usr/share/pixmaps/gdm-foot-logo.png
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/ServAuthDir to string /var/lib/gdm
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/ShowXtermFailsafeSession to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/GtkModulesList to string <NULL>
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/BaseXsession to string /etc/gdm/Xsession
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLabel0 to string Spezial_0
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/BackgroundProgramRestartDelay to integer 30
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLabel1 to string Spezial_1
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key daemon/DefaultPath to string /usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/games
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key gui/GtkRC to string /usr/share/themes/Default/gtk-2.0/gtkrc
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLabel2 to string Spezial_2
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key security/NeverPlaceCookiesOnNFS to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/UseCirclesInEntry to boolean false
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLabel3 to string Spezial_3
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLabel4 to string Spezial_4
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLabel5 to string Spezial_5
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLabel6 to string Spezial_6
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLabel7 to string Spezial_7
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key greeter/BackgroundScaleToFit to boolean true
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key customcommand/CustomCommandLabel8 to string Spezial_8
Jul  1 21:14:18 lenovo-t61 gdm[3431]: set config key security/RelaxPermissions to integer 1
Jul  1 21:14:18 lenovo-t61 gdm[3431]: gdm_main: Here we go...
Jul  1 21:14:18 lenovo-t61 gdm[3431]: gdm_start_first_unborn_local: Starting :0
Jul  1 21:14:18 lenovo-t61 gdm[3431]: gdm_display_manage: Managing :0
Jul  1 21:14:18 lenovo-t61 gdm[3431]: loop check: last_start 0, last_loop 0, now: 1183317258, retry_count: 0
Jul  1 21:14:18 lenovo-t61 gdm[3431]: Resetting counts for loop of death detection
Jul  1 21:14:18 lenovo-t61 gdm[3614]: gdm_slave_start: Starting slave process for :0
Jul  1 21:14:18 lenovo-t61 gdm[3614]: gdm_slave_start: Loop Thingie
Jul  1 21:14:18 lenovo-t61 gdm[3614]: Sending VT_NUM == -1 for slave 3614
Jul  1 21:14:18 lenovo-t61 gdm[3431]: gdm_display_manage: Forked slave: 3614
Jul  1 21:14:18 lenovo-t61 gdm[3431]: Handling message: 'VT_NUM 3614 -1'
Jul  1 21:14:18 lenovo-t61 gdm[3431]: Got VT_NUM == -1
Jul  1 21:14:18 lenovo-t61 gdm[3614]: gdm_server_start: :0
Jul  1 21:14:18 lenovo-t61 gdm[3614]: gdm_auth_secure_display: Setting up access for :0
Jul  1 21:14:18 lenovo-t61 gdm[3614]: gdm_auth_secure_display: Setting up access
Jul  1 21:14:18 lenovo-t61 gdm[3614]: gdm_auth_secure_display: Setting up access for :0 - 1 entries
Jul  1 21:14:18 lenovo-t61 gdm[3614]: Sending COOKIE == <secret> for slave 3614
Jul  1 21:14:18 lenovo-t61 gdm[3431]: Handling message: 'COOKIE 3614 92...'
Jul  1 21:14:18 lenovo-t61 gdm[3431]: Got COOKIE == <secret>
Jul  1 21:14:18 lenovo-t61 gdm[3614]: Sending AUTHFILE == <secret> for slave 3614
Jul  1 21:14:18 lenovo-t61 gdm[3431]: Handling message: 'AUTHFILE 3614 /var/lib/gdm/:0.Xauth'
Jul  1 21:14:18 lenovo-t61 gdm[3431]: Got AUTHFILE == /var/lib/gdm/:0.Xauth
Jul  1 21:14:18 lenovo-t61 gdm[3617]: gdm_server_spawn: '/usr/bin/X :0 -dpi 96 -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7'
Jul  1 21:14:18 lenovo-t61 gdm[3614]: gdm_server_spawn: Forked server on pid 3617
Jul  1 21:14:18 lenovo-t61 gdm[3614]: do_server_wait: Before mainloop waiting for server
Jul  1 21:14:18 lenovo-t61 gdm[3614]: gdm_server_start: After mainloop waiting for server
Jul  1 21:14:18 lenovo-t61 gdm[3614]: gdm_server_start: Completed :0!
Jul  1 21:14:18 lenovo-t61 gdm[3614]: Sending VT_NUM == 7 for slave 3614
Jul  1 21:14:18 lenovo-t61 gdm[3431]: Handling message: 'VT_NUM 3614 7'
Jul  1 21:14:18 lenovo-t61 gdm[3431]: Got VT_NUM == 7
Jul  1 21:14:18 lenovo-t61 gdm[3614]: Sending XPID == 3617 for slave 3614
Jul  1 21:14:18 lenovo-t61 gdm[3431]: Handling message: 'XPID 3614 3617'
Jul  1 21:14:18 lenovo-t61 gdm[3431]: Got XPID == 3617
Jul  1 21:14:18 lenovo-t61 gdm[3614]: gdm_slave_run: Opening display :0
Jul  1 21:14:21 lenovo-t61 gdm[3431]: Handling message: 'START_NEXT_LOCAL'
Jul  1 21:14:21 lenovo-t61 gdm[3614]: Xinerama active, but <= 0 screens?
Jul  1 21:14:21 lenovo-t61 gdm[3614]: slave killing self
Jul  1 21:14:21 lenovo-t61 gdm[3614]: term_quit: Final cleanup
Jul  1 21:14:21 lenovo-t61 gdm[3614]: gdm_slave_quick_exit: Will kill everything from the display
Jul  1 21:14:21 lenovo-t61 gdm[3614]: gdm_server_stop: Server for :0 going down!
Jul  1 21:14:21 lenovo-t61 gdm[3614]: gdm_server_stop: Killing server pid 3617
Jul  1 21:14:21 lenovo-t61 gdm[3614]: gdm_server_stop: Server pid 3617 dead
Jul  1 21:14:21 lenovo-t61 gdm[3614]: gdm_slave_quick_exit: Killed everything from the display
Jul  1 21:14:21 lenovo-t61 gdm[3431]: mainloop_sig_callback: Got signal 17
Jul  1 21:14:21 lenovo-t61 gdm[3431]: gdm_cleanup_children: child 3614 returned 4
Jul  1 21:14:21 lenovo-t61 gdm[3431]: gdm_child_action: Abbruch von Anzeige :0
Jul  1 21:14:21 lenovo-t61 gdm[3431]: gdm_display_unmanage: Stopping :0 (slave pid: 0)
Jul  1 21:14:21 lenovo-t61 gdm[3431]: gdm_display_unmanage: Display stopped
Jul  1 21:14:29 lenovo-t61 gdm[3431]: mainloop_sig_callback: Got signal 15
Jul  1 21:14:29 lenovo-t61 gdm[3431]: mainloop_sig_callback: Got TERM/INT. Going down!
Jul  1 21:14:29 lenovo-t61 gdm[3431]: gdm_final_cleanup
Jul  1 21:14:29 lenovo-t61 gdm[3431]: gdm_display_unmanage: Stopping :0 (slave pid: 0)
Jul  1 21:14:29 lenovo-t61 gdm[3431]: gdm_display_unmanage: Display stopped


X runs flawlessy through startx btw...hope someone has a solution to this

---

