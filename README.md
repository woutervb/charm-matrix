[![pipeline status](https://git.ec0.io/alchemy-charmers/charm-matrix/badges/master/pipeline.svg)](https://git.ec0.io/alchemy-charmers/charm-matrix/commits/master)                                                                  
[![coverage report](https://git.ec0.io/alchemy-charmers/charm-matrix/badges/master/coverage.svg)](https://git.ec0.io/alchemy-charmers/charm-matrix/commits/master)

Matrix
======

This charm will deploy a Matrix homeserver, running synapse, and optionally supporting the following bridges -
* matrix-appservice-irc

Deployment
==========

This charm currently relies on the following snaps being built locally and then deployed as resources:
* [snap-matrix-synapse - merged upstream](https://github.com/matrix-org/matrix-synapse) (ensure PR #6315 and #6317 are also merged into your local branch)
* [snap-matrix-appservice-irc - in review](https://github.com/matrix-org/matrix-appservice-irc/pull/807)

None of these charms are currently published to to store, pending further discussions upstream.
There is nothing preventing them from being hosted on the store, however the most sensible
namespaces are already registered, and working with the upstream project to get them pushing
automatically on merge is the desired outcome.
In the meantime, layer-snap provides the ability to upload the built charms as resources, where they will be deployed locally.
This means the level of confinement is lower (devmode instead of strict), and updates need to be
controlled by updating the uploaded snap resource, so getting these published on the store is
definitely on the roadmap for this charm.

Configuration
=============

This charm supports a number of configuration items for customising the behaviour of the homeserver.
These are documented in the `config.yaml` file, however the following are the most important:

* `enable-registration` controls whether or not public users can register an account.
* `server-name` controls the FQDN of the server used in federation and other client operations.
* `shared-secret` allows you to provide a shared secret which is used when registering users, if enabled.
* `enable-irc` installs and configures the IRC bridge when set to true.

Do ensure you review the remainder of the configuration items, as they control security and privacy related aspects of Synapse, and the
defaults might not suit your needs, erring on the side of privacy.

TODO
====

* matrix-appservice-slack support (WIP)
* matrix-puppet-slack support (WIP)

Author
======

This charm and the related snap work has been written by [James Hebden](mailto:james+matrix@ec0.io) of the Alchemy Charmers group.

Primary development is done on the [Alchemy Charmers GitLab](https://git.ec0.io/alchemy-charmers), and mirrored to [GitHub](https://github.com/alchemy-charmers).
