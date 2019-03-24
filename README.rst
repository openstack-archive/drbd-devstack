=============
drbd-devstack
=============

DRBD installation helper for DevStack.

* Free software: Apache license

This plugin helps to install the DRBD backend for Cinder 
(and, later on, Nova) in a devstack install.

Usage
-----

Put some lines similar to these in your `local.conf`:

    enable_plugin drbd-devstack https://git.openstack.org/openstack/drbd-devstack
    CINDER_ENABLED_BACKENDS=drbd:drbdmanage


A few environment variables can be set to modify the behaviour:

  * `CINDER_DRBD_NO_STORAGE` means `--no-storage`
  * `CINDER_DRBD_NO_CV` gets translated to `--no-control-volume`.
    This is allowed only for additional nodes, and not the initial drbdmanage node that *has* to create a control volume.
  * `CINDER_DRBD_USE_DRBD_PROTOCOL` makes the driver use the DRBD protocol to provide storage to the Nova nodes.


Secondary nodes are detected by having `$SERVICE_HOST` unequal to `$HOST_IP`, and therefore register themselves as additional nodes in drbdmanage.
