---
title: "xmonad logout after opening of firefox"
date: 2017-05-05
forum: Desktop Environments
---

### Post by mrityunjay23 on 2017-05-05
I am new Xmonad user. I have installed Xmonad thorough Software center.

When I open firefox in ubuntu Genome Xmonad through command prompt (firefox &) then it gives following error on command prompt. After little time my Xomand gets log out.

```
mrityunjay@mrityunjay-A7GMX-K:~$ firefox &
[1] 5546
mrityunjay@mrityunjay-A7GMX-K:~$ 
(process:5546): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed

(firefox:5546): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised

(firefox:5546): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised

(firefox:5546): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised

(firefox:5546): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised
console.error: youtubetmadblock: 
Object
    - message = Component returned failure code: 0x80520012 (NS_ERROR_FILE_NOT_FOUND) [nsIXPCComponents_Utils.import]
    - fileName = undefined
    - lineNumber = 3
    - stack = @undefined:3:NaN|@resource://jid1-w4wg5njhx4ljzr-at-jetpack/main/firefox/firefox.js:3:20|@resource://jid1-w4wg5njhx4ljzr-at-jetpack/main/youtube.js:2:49|run@resource://gre/modules/commonjs/sdk/addon/runner.js:145:19|startup/</<@resource://gre/modules/commonjs/sdk/addon/runner.js:86:7|Handler.prototype.process@resource://gre/modules/Promise-backend.js:867:23|this.PromiseWalker.walkerLoop@resource://gre/modules/Promise-backend.js:746:7|this.PromiseWalker.scheduleWalkerLoop/<@resource://gre/modules/Promise-backend.js:688:37|openModalWindow@resource://gre/components/nsPrompter.js:370:5|ModalPrompter.prototype.openPrompt@resource://gre/components/nsPrompter.js:553:9|ModalPrompter.prototype.nsIPrompt_promptUsernameAndPassword@resource://gre/components/nsPrompter.js:747:9|ModalPrompter.prototype.promptAuth@resource://gre/components/nsPrompter.js:846:18|Prompter.prototype.promptAuth@resource://gre/components/nsPrompter.js:108:16|LoginManagerPrompter.prototype.promptAuth@resource://gre/components/nsLoginManagerPrompter.js:597:12|LoginManagerPromptFactory.prototype._doAsyncPrompt/runnable.run@resource://gre/components/nsLoginManagerPrompter.js:107:16|
    - toString = function () /* use strict */ toString
console.error: youtubetmadblock: 
Object
    - message = Component returned failure code: 0x80520012 (NS_ERROR_FILE_NOT_FOUND) [nsIXPCComponents_Utils.import]
    - fileName = undefined
    - lineNumber = 3
    - stack = @undefined:3:NaN|@resource://jid1-w4wg5njhx4ljzr-at-jetpack/main/firefox/firefox.js:3:20|@resource://jid1-w4wg5njhx4ljzr-at-jetpack/main/youtube.js:2:49|run@resource://gre/modules/commonjs/sdk/addon/runner.js:145:19|startup/</<@resource://gre/modules/commonjs/sdk/addon/runner.js:86:7|Handler.prototype.process@resource://gre/modules/Promise-backend.js:867:23|this.PromiseWalker.walkerLoop@resource://gre/modules/Promise-backend.js:746:7|this.PromiseWalker.scheduleWalkerLoop/<@resource://gre/modules/Promise-backend.js:688:37|openModalWindow@resource://gre/components/nsPrompter.js:370:5|ModalPrompter.prototype.openPrompt@resource://gre/components/nsPrompter.js:553:9|ModalPrompter.prototype.nsIPrompt_promptUsernameAndPassword@resource://gre/components/nsPrompter.js:747:9|ModalPrompter.prototype.promptAuth@resource://gre/components/nsPrompter.js:846:18|Prompter.prototype.promptAuth@resource://gre/components/nsPrompter.js:108:16|LoginManagerPrompter.prototype.promptAuth@resource://gre/components/nsLoginManagerPrompter.js:597:12|LoginManagerPromptFactory.prototype._doAsyncPrompt/runnable.run@resource://gre/components/nsLoginManagerPrompter.js:107:16|
    - toString = function () /* use strict */ toString
console.error: adblockforyoutube: 
Object
    - message = Component returned failure code: 0x80520012 (NS_ERROR_FILE_NOT_FOUND) [nsIXPCComponents_Utils.import]
    - fileName = undefined
    - lineNumber = 18
    - stack = @undefined:18:NaN|@resource://jid1-q4sg8pyhq8kghs-at-jetpack/lib/firefox/firefox.js:18:20|@resource://jid1-q4sg8pyhq8kghs-at-jetpack/lib/common.js:3:13|run@resource://gre/modules/commonjs/sdk/addon/runner.js:145:19|startup/</<@resource://gre/modules/commonjs/sdk/addon/runner.js:86:7|Handler.prototype.process@resource://gre/modules/Promise-backend.js:867:23|this.PromiseWalker.walkerLoop@resource://gre/modules/Promise-backend.js:746:7|this.PromiseWalker.scheduleWalkerLoop/<@resource://gre/modules/Promise-backend.js:688:37|openModalWindow@resource://gre/components/nsPrompter.js:370:5|ModalPrompter.prototype.openPrompt@resource://gre/components/nsPrompter.js:553:9|ModalPrompter.prototype.nsIPrompt_promptUsernameAndPassword@resource://gre/components/nsPrompter.js:747:9|ModalPrompter.prototype.promptAuth@resource://gre/components/nsPrompter.js:846:18|Prompter.prototype.promptAuth@resource://gre/components/nsPrompter.js:108:16|LoginManagerPrompter.prototype.promptAuth@resource://gre/components/nsLoginManagerPrompter.js:597:12|LoginManagerPromptFactory.prototype._doAsyncPrompt/runnable.run@resource://gre/components/nsLoginManagerPrompter.js:107:16|
    - toString = function () /* use strict */ toString
console.error: adblockforyoutube: 
Object
    - message = Component returned failure code: 0x80520012 (NS_ERROR_FILE_NOT_FOUND) [nsIXPCComponents_Utils.import]
    - fileName = undefined
    - lineNumber = 18
    - stack = @undefined:18:NaN|@resource://jid1-q4sg8pyhq8kghs-at-jetpack/lib/firefox/firefox.js:18:20|@resource://jid1-q4sg8pyhq8kghs-at-jetpack/lib/common.js:3:13|run@resource://gre/modules/commonjs/sdk/addon/runner.js:145:19|startup/</<@resource://gre/modules/commonjs/sdk/addon/runner.js:86:7|Handler.prototype.process@resource://gre/modules/Promise-backend.js:867:23|this.PromiseWalker.walkerLoop@resource://gre/modules/Promise-backend.js:746:7|this.PromiseWalker.scheduleWalkerLoop/<@resource://gre/modules/Promise-backend.js:688:37|openModalWindow@resource://gre/components/nsPrompter.js:370:5|ModalPrompter.prototype.openPrompt@resource://gre/components/nsPrompter.js:553:9|ModalPrompter.prototype.nsIPrompt_promptUsernameAndPassword@resource://gre/components/nsPrompter.js:747:9|ModalPrompter.prototype.promptAuth@resource://gre/components/nsPrompter.js:846:18|Prompter.prototype.promptAuth@resource://gre/components/nsPrompter.js:108:16|LoginManagerPrompter.prototype.promptAuth@resource://gre/components/nsLoginManagerPrompter.js:597:12|LoginManagerPromptFactory.prototype._doAsyncPrompt/runnable.run@resource://gre/components/nsLoginManagerPrompter.js:107:16|
    - toString = function () /* use strict */ toString
mrityunjay@mrityunjay-A7GMX-K:~$ 

```


When I open firefox in ubuntu default through command prompt (firefox &) then it gives following error on command prompt.
```
(process:6582): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
```

How to get rid of Xmonad log out case and firefox error?

---

