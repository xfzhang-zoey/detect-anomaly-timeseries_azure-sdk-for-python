# Microsoft Azure SDK for Python

This is the Microsoft Azure {{package_pprint_name}} Client Library.
This package has been tested with Python 3.7+.
For a more complete view of Azure libraries, see the [azure sdk python release](https://aka.ms/azsdk/python/all).

## _Disclaimer_

_Azure SDK Python packages support for Python 2.7 has ended 01 January 2022. For more information and questions, please refer to https://github.com/Azure/azure-sdk-for-python/issues/20691_

## Getting started

### Prerequisites

- Python 3.7+ is required to use this package.
- [Azure subscription](https://azure.microsoft.com/free/)

### Install the package

```bash
pip install {{package_name}}
pip install azure-identity
```

### Authentication

By default, [Azure Active Directory](https://aka.ms/awps/aad) token authentication depends on correct configure of following environment variables.

- `AZURE_CLIENT_ID` for Azure client ID.
- `AZURE_TENANT_ID` for Azure tenant ID.
- `AZURE_CLIENT_SECRET` for Azure client secret.
{% if not no_sub %}
In addition, Azure subscription ID can be configured via environment variable `AZURE_SUBSCRIPTION_ID`.
{% endif %}
With above configuration, client can be authenticated by following code:

```python
from azure.identity import DefaultAzureCredential
from {{package_name | replace("-", ".")}} import {{ title }}
{% if not no_sub -%}
import os

sub_id = os.getenv("AZURE_SUBSCRIPTION_ID")
client = {{ title }}(credential=DefaultAzureCredential(), subscription_id=sub_id)
{% else %}
client = {{ title }}(credential=DefaultAzureCredential())
{% endif -%}
```

## Examples
{% if is_arm %}
{%- if not sample_link %}
{%- set sample_link="https://aka.ms/azsdk/python/mgmt/samples" %}
{% else %}
{%- set sample_link="https://github.com/Azure-Samples/azure-samples-python-management/tree/main/samples/" + sample_link %}
{%- endif %}
Code samples for this package can be found at [{{package_pprint_name}}](https://docs.microsoft.com/samples/browse/?languages=python&term=Getting%20started%20-%20Managing&terms=Getting%20started%20-%20Managing) on docs.microsoft.com and [Samples Repo]({{ sample_link }})
{% else %}
For code examples, see [{{package_pprint_name}}](https://docs.microsoft.com/python/api/overview/azure/{{package_doc_id}}) on docs.microsoft.com.
{% endif %}

## Troubleshooting

## Next steps

## Provide Feedback

If you encounter any bugs or have suggestions, please file an issue in the
[Issues](https://github.com/Azure/azure-sdk-for-python/issues)
section of the project. 


![Impressions](https://azure-sdk-impressions.azurewebsites.net/api/impressions/azure-sdk-for-python%2F{{package_name}}%2FREADME.png)
