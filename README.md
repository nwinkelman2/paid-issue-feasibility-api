<!-- travis-commercial-api-storefront/v1 product=commercial_api_product_082c3f897c559c998480a5dbd01d19b62aade035 -->
# Paid Issue Feasibility API

Turn a public paid software issue into a deterministic feasibility brief before your team spends engineering time on it. The API scores feasibility, competition, and ambiguity; flags material risks; and identifies likely workstreams.

**$9.00/month** includes **100 analyses**. Additional analyses are **$0.10 each**.

[Subscribe and get an API key](https://buy.stripe.com/fZu3cwb6e6z302FgjjcMM0n)

After Stripe confirms the subscription, checkout redirects to the one-time key claim page. Save the key then; plaintext keys are not retained for later display.

## Request

```bash
curl --request POST 'https://travis-commercial-api.noah-winkelman2.workers.dev/v1/capability/commercial.public.bounty_feasibility' \
  --header 'Authorization: Bearer YOUR_API_KEY' \
  --header 'Content-Type: application/json' \
  --data '{
    "title": "Add resumable uploads to the SDK",
    "description": "Implement resumable uploads, add acceptance tests, document recovery behavior, and submit a pull request for the paid bounty.",
    "reward_amount": 1500,
    "competitor_count": 2
  }'
```

## Response

```json
{
  "ok": true,
  "market": "public_paid_software_issue",
  "feasibility_score": 64,
  "competition_score": 29,
  "ambiguity_score": 52,
  "risk_flags": [],
  "workstreams": ["api", "documentation", "testing"],
  "evidence": {
    "description_characters": 125,
    "distinct_terms": 19,
    "acceptance_signal_present": true,
    "deliverable_signal_present": true,
    "payment_signal_present": true,
    "customer_input_retained": false,
    "provider_calls": 0
  }
}
```

## Input contract

| Field | Type | Bounds |
|---|---:|---|
| `title` | string | 5–300 characters |
| `description` | string | 40–20,000 characters |
| `reward_amount` | number | 0–100,000,000 |
| `competitor_count` | integer | 0–1,000,000; optional |

The analysis uses only the submitted public issue text, makes no provider calls, and does not retain customer input. It is decision support, not a promise that a bounty will be won or paid.

[Machine-readable catalog](https://travis-commercial-api.noah-winkelman2.workers.dev/v1/commercial-api/catalog) · [Key claim endpoint](https://travis-commercial-api.noah-winkelman2.workers.dev/v1/commercial-api/claim)
