# Multisite Kickstarter for Neos

The Flownative Multisite Kickstarter is a simple generator for Neos sites. These sites are prepared to be used in a multi-site setup. That means they come with the needed roles, privileges and settings to be separate from an editors view, while still being served in the same Neos installation.

## Installation

`composer require flownative/neos-multisitekickstarter`

### Composer adjustment needed

This package kickstarts sites that depend on the *Wwwision.AssetConstraints* package created by Bastian Waidelich. This package is officially in an experimental state, and thus not available via packagist.

Additionally (at the time of writing), the original package is not compatible with Neos 3.x. Therefore a fork has been created, and a project using a site created with the kickstarter has to adjust it's *root composer manifest* by adding a *repositories* and a *require* entry as follows:

    "repositories": [
        {
            "type": "git",
            "url": "https://github.com/kdambekalns/Wwwision.AssetConstraints.git"
        }
    ],

    "require": {
        "wwwision/assetconstraints": "dev-neos3-compatibility",
    }

## Usage

### Kickstarting a site

To kickstart a site, use the following command:

`./flow kickstart:multisite --package-key Acme.AcmeCom --site-name www.acme.com`

This is the same as with the `kickstart:site` command, the difference lies in the internal settings and policy that are generated.

### Granting access to a site

Each site comes with a role that grants access to it. As soon as such a role is assigned to an editor, she can edit the site and access the related asset collection.

The `Neos.Neos:Administrator` role has access to all sites by default.

## Credits

Development of this package has been sponsored by Schwabe AG, Muttenz, Switzerland.

The setup this package creates is based on a blog post by Aske Ertmann: https://blog.ertmann.me/multi-site-access-restriction-with-neos-cms-9d5624126d5b.