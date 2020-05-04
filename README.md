# SBP Toolkit Service Group Infra

**IMPORTANT - this readme file is a work-in-progress version**

## General Information

This repository will deploy the fundamental infrastructure resources, across two Resource Groups:

- Core RG
  - KeyVault
  - Log Analytics Workspace
- Network RG
  - Network Security Groups
  - Route Table
  - Virtual Network
  - Virtual Network Peerings

During the deployment to the Core RG it will also enable:

- Activity Log collection to the Log Analytics Workspace
- Enable Azure Security Center Standard for the Subscription

## YAML Pipeline

The pipeline for this repository is defined in azure-pipelines.yml. It uses YAML templates for stages, jobs and steps, all of which are located in the ci folder.

The deployment to each Resource Group is defined in a separate YAML job temple. Please adjust those files to meet your scenario.

## Sources

The ARM templates used for deployments are downloaded as pipeline artifacts, from a separate repo in a separate project. The pipeline defined in this repository will require the ID of the remote pipeline and the remote project project to provided as variables:

- sourcesPipeline: ''
- sourcesProject: ''

## Locations

The deployment in the provided pipeline targets Azure West Europe region by default, please adjust this to meet your requirements.

## Lifecycle

The provided pipeline is prepared to deploy the infrastructure components to four environments in the DTAP street - Dev, Test, Acc and Prod. By default only Dev in enabled. To enable other environments uncomment respective sections in azure-pipelines.yml and provide parameter files in top-level folders. For example see dev001.
