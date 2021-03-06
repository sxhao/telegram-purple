Telegram-Purple
===============

Telegram-purple is a Libpurple plugin that adds support for the Telegram messenger. Its still in an early (pre-alpha) development stage, but already provides basic chat functionality and group chats.

The plugin is based on the library [Libtgl](https://github.com/vysheng/tgl), which was written by Vitaly Valtman <mail@vysheng.ru> and others, see (http://github.com/vysheng/tgl)

# Features

    - Secret Chats (See the section below for further information)
    - Chats/Group-Chats
        * Send/receive messages
        * Discover buddies/chats
        * Discover buddy state and info
    - Profile Pictures
        * Download and use profile pictures
    - Display Geo-Messages
    - Display Pictures
    - Adium Support


# Installation

Unfortunately there are no packages right now, so you need to compile it yourself:

## 1. Get this repository


        git clone --recursive https://github.com/majn/telegram-purple


## 2. Get all Dependencies


### Fedora

        sudo yum install gcc openssl-devel glib2-devel libpurple-devel


### Debian

        sudo apt-get install libssl-dev libglib2.0-dev libpurple-dev


### OpenSUSE

        sudo zypper install gcc glib glib-devel libpurple libpurple-devel zlib-devel openssl libopenssl-devel


## 3. Compile and install

        ./configure
        make
        sudo make install


# Usage

## First Login

After succesfully completing all steps mentioned in the installation instructions, you should restart Pidgin to ensure that the plugin is loaded. When everything went well, Telegram should show up in the account manager:

![Create a new Telegram account](http://h2079792.stratoserver.net/telegram-purple/res/install-1.png)

The username is your current phone number, including your full country prefix instead of a leading '0'. For Germany, this would be '+49' for example. Telegram will verify your phone number by sending you a verification code via sms. You will be prompted for this code, once that happens.

![Provide a phone number](http://h2079792.stratoserver.net/telegram-purple/res/install-2.png)
 
Now you should be able to see all your contacts and chats in your buddy list and send/receive messages.

## Using secret chats

You can use Telegram secret chats with this plugin, they will show up as a new buddy with a '!' in front of the buddy name.

One caveat of secret chats in Telegram is that they can only have one endpoint, this is a limitation of the protocol. This means that if you create a secret chat in Pidgin you will not be able to use that chat on your phone. You will be asked whether to accept each secret chat, so you can always choose to accept the chat on a different device if you want. You can set a default behavior for dealing with secret chats (Accept or Decline) in the account settings if you don't want that prompt to appear every time.

Self destructive messages will be ignored, since I don't know any way to delete them from the conversation and the history.

### Confirming the key authenticity

Click on the buddy in the buddy list and click on "Show Info" to visualize the key fingerprint.  

![Confirm key authenticity](http://h2079792.stratoserver.net/telegram-purple/res/key.png)

### Initiate secret chats

To initiate a secret chat from Pidgin, click on a Buddy in the Buddy List and hit ``Start Secret Chat''

### Deleting secret chat

If you delete a secret chat from the buddy list, it will be terminated and no longer be usable.


## Platform Support

We only provide an installation guide for Linux right now, even though it should be possible to compile this plugin on other platforms. If someone manages to create a working Windows or BSD-build please let us know.



# Troubleshooting

If you encounter problems running this plugin and you have updated from an older version,
deleting your old user-data might be helpful. WARNING: This will require you to enter a new authentication
code and delete all your secret chat keys.

To clean all your user files run:


        sudo make purge


# Adium Plugin

If you just want to use the plugin in Adium, [download precompiled packages here.](https://github.com/majn/telegram-purple/releases)

The bundles were tested to work on OSX 10.8 to 10.10. If it doesn't work on your installation
please send your Adium crash log (which you can find in ~/Library/Logs/Adium 2/).

## Building with XCode

1. Compile the source of your current Adium version and add the created frameworks to the Adium-Telegram build path.
2. Build the tgl submodule.
2. Get zlib and libcrypto.a and provide it somewhere in your build path.
3. Build the XCode-Project and execute the created bundle.


# Unicode Emojis for Pidgin

The Telegram phone applications for iOS and Android make use of standardized Unicode smileys (called [Emojis](https://en.wikipedia.org/wiki/Emoji)). Pidgin
does not display those smileys natively, but you can install a custom smiley theme like (https://github.com/stv0g/unicode-emoji) or (https://github.com/VxJasonxV/emoji-for-pidgin) and activate it under Settings > Themes > Smiley Theme.


# Changelog

Warning, this version is mainly for development and testing and NOT for productive use. Even though it already provides basic features, you should still expect bugs and crashes when running it.

When encountering a crash or some other bugs, please report it to us, preferably together with a backtrace of the crashed application [https://developer.pidgin.im/wiki/GetABacktrace]

## Version 0.6

    - Support for secret chats 
    - Receiving geo messages

## Version 0.5

    - Display incoming photos
    - Respect received user and chat property updates
    - Support changing own profile picture
    - Support adding new contacts
    - Display service messages
    - Works with libpurple proxy settings

## TODO:

    - Picture Uploads
    - Audio, Video and File Transfers

# Authors

Telegram-Purple and Telegram-Adium were written by:

    - Matthias Jentsch <mtthsjntsch@gmail.com>
    - Christopher Althaus <althaus.christopher@gmail.com>
    - Markus Endres <endresma45241@th-nuernberg.de>
    - Vitaly Valtman
